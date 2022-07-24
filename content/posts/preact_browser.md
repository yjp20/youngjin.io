---
title: "Using Preact without build tools"
date: 2020-05-03T22:14:57-06:00
tags: ["code"]
draft: false
---

One of the things I don't like the most about frameworks like React and Preact is that you lose some of the immediacy of the web by using clunky build tools. Before you can start programming, you have to write up a webpack configuration and have to deal with building the code every time. Sure, newer, streamlined CLI tools make it easier to deal with it, but it's still a compromise to one of native web development's greatest pedagolgoical features -- a short feedback loop.

While most of the JS community is used to using Webpack, it's not necessary. In fact, I would argue that it's a much better experience for new developers to write code for the browser directly.

## Getting Preact on the Browser

### Modules?

ES6 presents a new way to define and import modules, which should allow proper dependency resolution in the near future. At least with webpack, the following code would work.

```js
import { Component, h, render } from 'preact'
```

Unfortunately, importing from `'preact'` doesn't work directly on the browser, since it doesn't know what the symbol `preact` points to. As of May 2020, only direct links to the module resources are accepted. Module resources are generally denoted by the suffix `.mjs`, although `.js` is sometimes still used.

```js
import { Component, h, render } from 'https://unpkg.com/preact/dist/preact.mjs'
```

Even this has it's limits. Some `.mjs` files are written with import statements such as `import defaultExport from 'module'`. For example, importing from `https://unpkg.com/preact/debug/dist/debug.mjs` will not work on the browser, as it depends on `preact` and `preact-devtools`. By the way, I would strongly recommend having `preact-debug` if you're going to be developing with Preact.

### Universal Module Definition

The best option, for now, are UMD files, which are compiled in such a way that it is compatible with both the backend and frontend. "Importing" a UMD module just consists of adding it to the html inside of a script tag, the good old way.

```html
<script src="https://unpkg.com/preact/dist/preact.umd.js"></script>
<script src="https://unpkg.com/preact/devtools/dist/devtools.umd.js"></script>
<script src="https://unpkg.com/preact/debug/dist/debug.umd.js"></script>
```

One thing to pay attention to UMD files on the browser does not automatically resolve dependencies. You have to add them yourself and you have to do them in the right order.

Then, you replace the import lines with code like the following. Noticably, instead of the import symbol, we use `window.[module name in camelcase]`.

```
var { Component, h, render } = window.preact
var { Router, route } = window.preactRouter
```

### The Future

A pending WICG spec, if passed, will introduce a way to map symbols like `'preact'` to a url, meaning that modules will finally begin to work properly on the browser. The proposal is extremely straightforward; read more [here](https://github.com/WICG/import-maps).

## htm

htm is essentially native jsx. If you've written JSX, you can write using htm. There's only a few essential differences, and it's just as powerful with minimal performance penalty.

```js
const html = window.htm.bind(h)

const App = function () {
	return html`<p> Hello </p>`
}

render(html`<${App} />`, document.body)
```

Wherever there would be JSX, you have a string literal with html. Wherever there used to be `{}`, you have `${}`.
