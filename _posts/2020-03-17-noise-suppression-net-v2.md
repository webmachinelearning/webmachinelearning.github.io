---
layout: post
title: 'Noise Suppression Net 2 (NSNet2)'
date: 2021-03-17 20:42:03 +0800
author: Web Machine Learning Working Group
avatar: https://avatars.githubusercontent.com/u/379216?s=200&v=4
categories: get-started
---

In the WebNN API, the [`Operand`](https://webmachinelearning.github.io/webnn/#operand) objects represent input, output, and constant multi-dimensional arrays known as [tensors](https://mathworld.wolfram.com/Tensor.html). The [`NeuralNetworkContext`](https://webmachinelearning.github.io/webnn/#api-neuralnetworkcontext) defines a set of operations that facilitate the construction and execution of this computational graph. Such operations may be accelerated with dedicated hardware such as the GPUs, CPUs with extensions for deep learning, or dedicated ML accelerators. These operations defined by the WebNN API are required by [models](https://github.com/webmachinelearning/webnn/blob/master/op_compatibility/first_wave_models.md) that address key application use cases. Additionally, the WebNN API provides affordances to builder a computational graph, compile the graph, execute the graph, and integrate the graph with other Web APIs that provide input data to the graph e.g. media APIs for image or video frames and sensor APIs for sensory data.

This [example](https://webmachinelearning.github.io/webnn/#examples) builds, compiles, and executes a graph comprised of three ops, takes four inputs and returns one output.

<!-- more -->

There are many important [application use cases](https://webmachinelearning.github.io/webnn/#usecases-application) for high-performance neural network inference. One such use case is deep-learning noise suppression (DNS) in web-based video conferencing. The following sample shows how the [NSNet2](https://github.com/microsoft/DNS-Challenge/tree/master/NSNet2-baseline) baseline implementation of deep learning-based noise suppression model may be implemented using the WebNN API.

```js
// Noise Suppression Net 2 (NSNet2) 
// Baseline Model for Deep Noise Suppression Challenge (DNS) 2021.
export class NSNet2 {
  constructor() {
    this.model = null;
    this.compiledModel = null;
    this.frameSize = 161;
    this.hiddenSize = 400;
  }

  async load(baseUrl, batchSize, frames) {
    const nn = navigator.ml.getNeuralNetworkContext();
    const builder = nn.createModelBuilder();
    // Create constants by loading pre-trained data from .npy files.
    const weight172 = await buildConstantByNpy(builder, baseUrl + '172.npy');
    const biasFcIn0 = await buildConstantByNpy(builder, baseUrl + 'fc_in_0_bias.npy');
    const weight192 = await buildConstantByNpy(builder, baseUrl + '192.npy');
    const recurrentWeight193 = await buildConstantByNpy(builder, baseUrl + '193.npy');
    const bias194 = await buildConstantByNpy(builder, baseUrl + '194_0.npy');
    const recurrentBias194 = await buildConstantByNpy(builder, baseUrl + '194_1.npy');
    const weight212 = await buildConstantByNpy(builder, baseUrl + '212.npy');
    const recurrentWeight213 = await buildConstantByNpy(builder, baseUrl + '213.npy');
    const bias214 = await buildConstantByNpy(builder, baseUrl + '214_0.npy');
    const recurrentBias214 = await buildConstantByNpy(builder, baseUrl + '214_1.npy');
    const weight215 = await buildConstantByNpy(builder, baseUrl + '215.npy');
    const biasFcOut0 = await buildConstantByNpy(builder, baseUrl + 'fc_out_0_bias.npy');
    const weight216 = await buildConstantByNpy(builder, baseUrl + '216.npy');
    const biasFcOut2 = await buildConstantByNpy(builder, baseUrl + 'fc_out_2_bias.npy');
    const weight217 = await buildConstantByNpy(builder, baseUrl + '217.npy');
    const biasFcOut4 = await buildConstantByNpy(builder, baseUrl + 'fc_out_4_bias.npy');
    // Build up the network.
    const input = builder.input('input', {type: 'float32', dimensions: [batchSize, frames, this.frameSize]});
    const relu20 = builder.relu(builder.add(builder.matmul(input, weight172), biasFcIn0));
    const transpose31 = builder.transpose(relu20, {permutation: [1, 0, 2]});
    const initialState92 = builder.input('initialState92', {type: 'float32', dimensions: [1, batchSize, this.hiddenSize]});
    const [gru94, gru93] = builder.gru(transpose31, weight192, recurrentWeight193, frames, this.hiddenSize,
        {bias: bias194, recurrentBias: recurrentBias194, initialHiddenState: initialState92, returnSequence: true});
    const squeeze95 = builder.squeeze(gru93, {axes: [1]});
    const initialState155 = builder.input('initialState155', {type: 'float32', dimensions: [1, batchSize, this.hiddenSize]});
    const [gru157, gru156] = builder.gru(squeeze95, weight212, recurrentWeight213, frames, this.hiddenSize,
        {bias: bias214, recurrentBias: recurrentBias214, initialHiddenState: initialState155, returnSequence: true});
    const squeeze158 = builder.squeeze(gru156, {axes: [1]});
    const transpose159 = builder.transpose(squeeze158, {permutation: [1, 0, 2]});
    const relu163 = builder.relu(builder.add(builder.matmul(transpose159, weight215), biasFcOut0));
    const relu167 = builder.relu(builder.add(builder.matmul(relu163, weight216), biasFcOut2));
    const output = builder.sigmoid(builder.add(builder.matmul(relu167, weight217), biasFcOut4));
    this.model = builder.createModel({output, gru94, gru157});
  }

  async compile(options) {
    this.compiledModel = await this.model.compile(options);
  }

  async compute(inputBuffer, initialState92Buffer, initialState155Buffer) {
    const inputs = {
      input: {buffer: inputBuffer},
      initialState92: {buffer: initialState92Buffer},
      initialState155: {buffer: initialState155Buffer},
    };
    return await this.compiledModel.compute(inputs);
  }
}
```

Try the live version of the [WebNN NSNet2 example](https://webmachinelearning.github.io/webnn-samples/nsnet2/).  This live version builds upon [nsnet2.js](https://github.com/webmachinelearning/webnn-samples/blob/master/nsnet2/nsnet2.js) that implements the above code snippet as a JS module.