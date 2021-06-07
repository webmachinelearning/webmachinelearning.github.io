---
layout: post
title: 'Build Your First Graph with WebNN API'
date: 2021-03-15 20:42:03 +0800
author: Web Machine Learning Working Group
avatar: https://avatars.githubusercontent.com/u/379216?s=200&v=4
categories: get-started
---

A core abstraction behind popular neural networks is a
computational graph, a directed graph with its nodes corresponding to
operations (ops) and input variables. One node’s output value is the input
to another node. 

The WebNN API brings this abstraction to the web.

In the WebNN API, the Operand objects represent
input, output, and constant multi-dimensional arrays known
as tensors. The NeuralNetworkContext defines a set of operations
that facilitate the construction and execution of this computational
graph. Such operations may be accelerated with dedicated hardware such as
the GPUs, CPUs with extensions for deep learning, or dedicated
ML accelerators. These operations defined by the WebNN API are required
by models that address key application use cases. 

<!-- more -->

Additionally,
the WebNN API provides affordances to builder a computational graph,
compile the graph, execute the graph, and integrate the graph with other Web
APIs that provide input data to the graph e.g. media APIs for image or
video frames and sensor APIs for sensory data.

This example builds,
compiles, and executes a graph comprised of three ops, takes four inputs
and returns one output:

```js
const context = navigator.ml.createContext({powerPreference: 'low-power'});

// The following code builds a graph as:
// constant1 ---+
//              +--- Add ---> intermediateOutput1 ---+
// input1    ---+                                    |
//                                                   +--- Mul---> output
// constant2 ---+                                    |
//              +--- Add ---> intermediateOutput2 ---+
// input2    ---+

// Use tensors in 4 dimensions.
const TENSOR_DIMS = [1, 2, 2, 2];
const TENSOR_SIZE = 8;

const builder = new MLGraphBuilder(context);

// Create OperandDescriptor object.
const desc = {type: 'float32', dimensions: TENSOR_DIMS};

// constant1 is a constant operand with the value 0.5.
const constantBuffer1 = new Float32Array(TENSOR_SIZE).fill(0.5);
const constant1 = builder.constant(desc, constantBuffer1);

// input1 is one of the input operands. Its value will be set before execution.
const input1 = builder.input('input1', desc);

// constant2 is another constant operand with the value 0.5.
const constantBuffer2 = new Float32Array(TENSOR_SIZE).fill(0.5);
const constant2 = builder.constant(desc, constantBuffer2);

// input2 is another input operand. Its value will be set before execution.
const input2 = builder.input('input2', desc);

// intermediateOutput1 is the output of the first Add operation.
const intermediateOutput1 = builder.add(constant1, input1);

// intermediateOutput2 is the output of the second Add operation.
const intermediateOutput2 = builder.add(constant2, input2);

// output is the output operand of the Mul operation.
const output = builder.mul(intermediateOutput1, intermediateOutput2);

// Build graph.
const graph = await builder.build({'output': output});

// Setup the input buffers with value 1.
const inputBuffer1 = new Float32Array(TENSOR_SIZE).fill(1);
const inputBuffer2 = new Float32Array(TENSOR_SIZE).fill(1);

// Asynchronously execute the built model with the specified inputs.
const inputs = {
  'input1': {data: inputBuffer1},
  'input2': {data: inputBuffer2},
};
const outputs = await graph.compute(inputs);

// Log the shape and computed result of the output operand.
console.log('Output shape: ' + outputs.output.dimensions);
// Output shape: 1,2,2,2
console.log('Output value: ' + outputs.output.data);
// Output value: 2.25,2.25,2.25,2.25,2.25,2.25,2.25,2.25
```

Try the live version of the [WebNN simple graphs example](hhttps://webmachinelearning.github.io/webnn-samples/code/).