---
layout: post
title: 'Try out WebNN API early using WebNN Polyfill'
date: 2022-12-08 10:42:03 +0800
author: Wanming Lin, Bruce Dai
avatar: https://avatars.githubusercontent.com/u/42399997?s=200&v=4
categories: blog
---

The [WebNN Polyfill][polyfill] has been published to NPM.

It is a JavaScript implementation of the WebNN API, based on
[TensorFlow.js][tfjs] that supports multiple backends for both
Web browsers and Node.js.


With this polyfill, Web developers are able to experience the WebNN API
early before the native implementations are shipped. Meanwhile, it can
be treated as an independent implementation to help validate the feasibility
and stability of the WebNN specification.

<!-- more -->

## Usage

Import the package via either NPM or a script tag.

- Via NPM

```js
import '@webmachinelearning/webnn-polyfill';
```

- Via a script tag

```html
<script src="https://cdn.jsdelivr.net/npm/@webmachinelearning/webnn-polyfill/dist/webnn-polyfill.js"></script>
```

Before using WebNN API, you should set backend to enable TensorFlow.js as follows.
Currently WebNN Polyfill supports 3 backends: `CPU`, `WebGL` and `WASM`. `CPU` backend
has higher numerical precision, while `WebGL` backend provides better performance.
A new backend `WebGPU` is work in progress.

```js
    const backend = 'webgl'; // or 'cpu', 'wasm'
    const context = await navigator.ml.createContext();
    const tf = context.tf;
    await tf.setBackend(backend);
    await tf.ready();
```

## Samples

Try out the live version of [WebNN samples][samples] which fall back to the
WebNN Polyfill in the browser without native WebNN API support. These samples
showcase various popular use cases for neural networks powered by WebNN API.

## Vision

We will continuously develop the WebNN Polyfill to keep it aligned with the WebNN API
spec. At the same time, WebNN API development in [Chromium][webnn in chromium]
is in full swing, we hope it won't take too long to bring hardware acceleration
access to Web developers through WebNN API.


[polyfill]: https://www.npmjs.com/package/@webmachinelearning/webnn-polyfill
[tfjs]: https://github.com/tensorflow/tfjs
[samples]: https://webmachinelearning.github.io/webnn-samples/
[webnn in chromium]: https://bugs.chromium.org/p/chromium/issues/detail?id=1273291
