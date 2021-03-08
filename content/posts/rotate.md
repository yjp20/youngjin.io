---
title: "Rotate an image using Javascript in the browser"
date: 2020-08-25T23:24:27+09:00
tags: ["code"]
draft: false
---

## Why?

Images uploaded up onto the web, especially now in the mobile age, often have the wrong orientation. It's not impossible to imagine that you might want to be able rotate these images from the client, rather than on the backend. At the very least, I needed to accomplish this task in my work place.

## Solutions

### image-orientation

Interestingly, there aren't many good, native ways to accomplish this task. The css `image-orientation` property promises to fix this issue, but it's only implemented in the newest of browsers and has recently been deprecated.

### css

Rotating by css is possible, but it's very difficult to get right. Because the transform property in css makes the object itself rotate but not the document flow, the logic for rotation becomes very complicated and therefore (nearly?) impossible to accomplish with pure css. This method works fine if you have a square, but if the aspect ratio is not perfectly one, then no matter what you do it will not stay within the boundaries of the container. Furthermore, making a solution like this responsive will introduce overhead in both performance and complexity.

### (recommended) js solution

Here's what I promised, a way to rotate an image without the image clipping out of the boundaries and reacting to the size of the container responsively. First, the code.

```js
function rotateImage(src, rotation) {
  rotation %= 360;
  return new Promise((resolve) => {
    const sideways = rotation === 90 || rotation === 270;
    const canvas = document.createElement("canvas");

    const image = new Image();
    image.setAttribute("crossorigin", "anonymous");
    image.onload = () => {
      const width = sideways ? image.height : image.width;
      const height = sideways ? image.width : image.height;

      const ctx = canvas.getContext("2d");
      if (!ctx) return;
      canvas.width = width;
      canvas.height = height;

      ctx.translate(width / 2, height / 2);
      ctx.rotate((Math.PI / 180) * rotation);
      ctx.drawImage(image, -image.width / 2, -image.height / 2);
      canvas.toBlob((blob) => {
        const url = URL.createObjectURL(blob);
        resolve(url);
      });
    };
    image.onerror = () => {
      resolve(src);
    };
    if (src) image.src = src;
  });
};
```

What this code does is uses the canvas to, first, rotate the image within the canvas, then second, use that canvas to create an objectUrl that can be used within your code as an image. The "rotation" only supports increments of 90 degrees.
