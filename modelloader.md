---
layout: page
title: Model Loader
permalink: /modelloader/
---

Model Loader is a proposed web API to load a custom, pre-trained machine learning model in a standard format, compile it for the available hardware, and apply it to example data in JavaScript in order to perform inference, like classification, regression, or ranking. The idea is to make it as easy as possible for web developers to use a custom, pre-built machine learning model in their web app, across devices and browsers.

<div class="herobar modelloader">
    <div class="buttons">
        <a class="button button--atlas getstarted" href="https://webmachinelearning.github.io/model-loader/"><span>Specification</span>
        <div class="marquee" aria-hidden="true">
            <div class="marqueeinner"><span>Specification</span><span>Specification</span><span>Specification</span><span>Specification</span></div>
        </div>
        </a><a class="button buttonwhite" href="https://github.com/webmachinelearning/model-loader/blob/master/explainer.md">Explainer</a>
    </div>
</div>

Performing inference locally can:

- Preserve privacy, by not shipping user data across the network
- Improve performance, by eliminating network latency
- Provide a fallback if network access is unavailable, possibly using a smaller and lower quality model
- The API is modeled after existing inference APIs like TensorFlow Serving, Clipper, TensorRT, and MXNet Model Server, which are already widely used by many products and organizations for large volumes of requests. Using an API that’s similar to a server-based API makes it easier to switch between server-based and local-based inference.

Unlike the Shape Detection API, the model loader APIs are generic. Application-specific libraries and APIs could be built on top.

The API does not support training a model, modifying a model, federated learning, or other functionality. Maybe future APIs could address those, if useful.