---
title: "Rotate an image using Javascript in the browser"
date: 2020-08-25T23:24:27+09:00
tags: ["code"]
draft: true
---

## Why?

Images uploaded up onto the web, especially now in the mobile age, often have the wrong orientation. It's not impossible to imagine that you might want to be able rotate these images from the client, rather than on the backend. At the very least, I needed to accomplish this task in my work place.

## Solutions

### image-orientation

Interestingly, there aren't many good, native ways to accomplish this task. The css `image-orientation` property promises to fix this issue, but it's only implemented in the newest of browsers and has recently been deprecated.

### css

Rotating by css is possible, but it's very difficult to get right. Because the transform property in css makes the object itself rotate, it makes the logic for rotation very complicated and therefore impossible to accomplish with pure css. This method works fine if you have a square, but if the aspect ratio is not perfectly one, then no matter what you do it will not stay within the boundaries of the container. Furthermore, making a solution like this responsive will introduce overhead in both performance and complexity.

### (recommended) js solution

Here's what I promised, a way to rotate an image without the image clipping out of the boundaries and reacting to the size of the container responsively. First, the code.

```

```





