---
layout: post
title: 'Introduction to Web Neural Network API (WebNN)'
date: 2024-05-16 14:55:22 +0100
author: Paul Cooper
avatar: https://avatars.githubusercontent.com/u/722868?s=200&v=4
categories: get-started
---

## Introduction to Web Neural Network API (WebNN)

The Web Neural Network API (WebNN) brings accelerated machine learning capabilities directly to web applications. With WebNN, developers can harness the power of neural networks within the browser environment, enabling a wide range of AI-driven use cases without relying on external servers or plugins.

### What is WebNN?

WebNN is a JavaScript API that provides a high-level interface for executing neural network inference tasks efficiently on various hardware accelerators, such as CPUs, GPUs, and dedicated AI chips (sometimes called NPUs or TPUs). By utilizing hardware acceleration, WebNN enables faster and more power-efficient execution of machine learning models, making it ideal for real-time applications and scenarios where latency is critical.

### Programming Model

WebNN follows a simple programming model, allowing developers to perform inference tasks with minimal complexity. The API is focused on defining the operations and infrastructure necessary to execute machine learning models, rather than handling higher-level functionalities such as model loading, parsing, or management. WebNN is designed to be agnostic to model formats and leaves the responsibility of loading and parsing models to other libraries (such as ONNX.js or Tensorflow.js) or the web application itself.

At a high level WebNN essentially has 2 steps to run a model:

* Model Construction: In WebNN the first step is to construct the model using the MLGraphBuilder API. Once the model has been constructed it can be built into an executable graph. 

* Model Execution: Once the executable graph has been constructed, data is input and the graph executes inference tasks to obtain predictions or classifications. WebNN provides methods for selecting backends (either explicitly or by characteristics) that then process the input data and return output results from the model.

WebNN leverages hardware accelerators to accelerate the execution of models. Since WebNN is hardware and model agnostic it can use any of the available hardware resources (whether CPU, GPU, NPU, TPU, etc), maximizing performance and minimizing latency, enabling smooth and responsive user experiences.

### Sample Code

Let's take a look at example pseudo-code that demonstrates how to perform inference using WebNN. In this example, we will show the basic API for model construction and execution. More details of model construction are covered in other tutorials.

```js
/* Create a context and MLGraphBuilder */
const context = await navigator.ml.createContext(/* execution parameters */);
const builder = new MLGraphBuilder(context);

/* Construct the model */
// WebNN supports a core set of ML operators - a full list can be found at 
// https://www.w3.org/TR/webnn/#api-mlgraphbuilder


/* Build executable graph */
const graph = await builder.build({'output': output});

/* Arrange input and output buffers */
const inputBuffer = new Float32Array(TENSOR_SIZE);
const outputBuffer = new Float32Array(TENSOR_SIZE);

const inputs = {'input': inputBuffer};

const outputs = {'output': outputBuffer};

/* Execute the compiled graph with the specified inputs. */
const results = await context.compute(graph, inputs, outputs);

console.log('Output values: ' + results.outputs.output);
```

This is a basic pseudo-code example of how to use WebNN API to construct a model and execute it. In a real-world scenario, you would replace the placeholders (/* Construct the model */, /* Arrange input and output buffers */, etc.) with actual model construction, input data, and execution parameters specific to your application. 

### Conclusion

WebNN opens up exciting possibilities for integrating machine learning capabilities into web applications, enabling developers to create innovative experiences powered by AI directly in the browser. With its simple programming model and support for hardware acceleration, WebNN empowers developers to build responsive and efficient AI-driven solutions that run seamlessly on a wide range of devices. 