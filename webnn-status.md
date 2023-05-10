---
layout: page
title: Implementation Status of WebNN Operations
permalink: /webnn-status/
---

<style>
.post img {
 width: 24px;
 height: 24px;
 margin: 0px 4px;
 transform: none;
 display: inline-block;
}

.post .onnxrt img {
 width: 80px;
}

.post .tflite img {
 width: 102px;
}

.post-content tbody td {
 padding: 4px 24px;
 vertical-align: middle;
}

.post-content tbody td br {
  height:  0px;
  display: none;
}

.impl_status {
   text-align: center;
   display: grid; 
   grid-template-columns: 1fr 1fr 1fr;
   gap: 0px;
   border: 1px solid #dfe2e5;
   padding: 10px;
   font-size: 0.9em;
}

.impl_status .title, .post-content table .title {
  font-weight: 400;
  font-size: 1rem;
}

.impl_status .title {
  margin-bottom: 0.4rem;
}

.impl_status div {
  margin: 0 12px;
}
</style>

| <br><span class="title">![W3C](https://www.w3.org/StyleSheets/TR/2021/logos/W3C)<br>[WebNN Spec](https://www.w3.org/TR/webnn/)</span> | <br><span class="title">Web Platform<br>Tests</span> | <span class="title">XNNPack/CPU<br>backend</span> <sup>[1]</sup> | <span class="title">External Delegate</span> <sup>[2]</sup> | <span class="title">Execution Provider</span> <sup>[3]</sup> | 
| ^^ | ^^ | ![Chrome Dev](https://raw.githubusercontent.com/alrra/browser-logos/main/src/chrome-dev/chrome-dev_24x24.png) ![Edge Canary](https://raw.githubusercontent.com/alrra/browser-logos/main/src/edge-canary/edge-canary_24x24.png) <sup>[4]</sup> | ![TensorFlow Lite](https://www.gstatic.com/devrel-devsite/prod/v8ec4d0a037302c47ae529ad4e3f06c9e782b3a31a381294b5a70403547dc6b12/tensorflow/images/lockup.svg) Lite {: class="tflite"}<br>for TensorFlow.js | ![ONNX Runtime Web](https://onnxruntime.ai/images/svg/ONNX-Runtime-logo.svg) {: class="onnxrt"} |
| ^^ | ^^ | ![Windows](https://wpt.fyi/static/win.svg) ![Linux](https://wpt.fyi/static/linux.svg) | ^^ | ^^ |
| -- | -- | -- | -- | -- |
| <span class="spec">[clamp](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-clamp)</span> | [📈](https://wpt.fyi/results/webnn/clamp.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/clamp.https.any.js) | <span class="x_s">✅</span> clamp | <span class="ed_s">✅</span> ReluN1To1 | <span class="ep_s">✅</span> Clip |
| ^^ | ^^ | <span class="ed_s">✅</span> Relu6 | ^^ | ^^ |
| <br><span class="spec">[concat](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-concat)</span> | [📈](https://wpt.fyi/results/webnn/concat.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/concat.https.any.js) | <span class="x_s">✅</span> concatenate2 | <br><span class="ed_s">✅</span> Concatenation | <br><span class="ep_s">✅</span> Concat |
| ^^ | ^^ | <span class="x_s">✅</span> concatenate3 | ^^ | ^^ |
| ^^ | ^^ | <span class="x_s">✅</span> concatenate4 | ^^ | ^^ |
| <span class="spec">[conv2d](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-conv2d)</span> | [📈](https://wpt.fyi/results/webnn/conv2d.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/conv2d.https.any.js) | <span class="x_s">✅</span> convolution_2d | <span class="ed_s">✅</span> Conv2d | <span class="ep_s">✅</span> Conv |
| ^^ | ^^ | ^^ | <span class="ed_s">✅</span> DepthwiseConv2d | ^^ |
| <span class="spec">[convTranspose2d](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-convtranspose2d)</span> | [📈](https://wpt.fyi/results/webnn/conv_transpose2d.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/conv_transpose2d.https.any.js) | <span class="x_s">✅</span> deconvolution_2d | <span class="ed_s">✅</span> TransposeConv | <span class="ep_s">✅</span> ConvTranspose |
| ^^ | ^^ | ^^ | <span class="ed_s">✅</span> Convolution2DTransposeBias | ^^ |
| <span class="spec">[add <sup>element-wise binary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-binary)</span> | [📈](https://wpt.fyi/results/webnn/elementwise_binary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_binary.https.any.js) | <span class="x_s">✅</span> add2 | <span class="ed_s">✅</span> Add | <span class="ep_s">✅</span> Add |
| <span class="spec">[sub <sup>element-wise binary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-binary)</span> | [📈](https://wpt.fyi/results/webnn/elementwise_binary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_binary.https.any.js) | <span class="x_s">✅</span> subtract | <span class="ed_s">✅</span> Sub | <span class="ep_s">✅</span> Sub |
| <span class="spec">[mul <sup>element-wise binary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-binary)</span> | [📈](https://wpt.fyi/results/webnn/elementwise_binary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_binary.https.any.js) | <span class="x_s">✅</span> multiply2 | <span class="ed_s">✅</span> Mul | <span class="ep_s">✅</span> Mul |
| <span class="spec">[div <sup>element-wise binary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-binary)</span> | [📈](https://wpt.fyi/results/webnn/clamp.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_binary.https.any.js) | <span class="x_s">✅</span> divide | <span class="ed_s">✅</span> Div | <span class="ep_s">✅</span> Div |
| <span class="spec">[max <sup>element-wise binary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-binary)</span> | [📈](https://wpt.fyi/results/webnn/elementwise_binary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_binary.https.any.js) | <span class="x_s">✅</span> maximum2 | <span class="ed_s">✅</span> Maximum | <span class="ep_wip">🚀</span> Max |
| <span class="spec">[min <sup>element-wise binary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-binary)</span> | [📈](https://wpt.fyi/results/webnn/elementwise_binary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_binary.https.any.js) | <span class="x_s">✅</span> minimum2 | <span class="ed_s">✅</span> Minimum | <span class="ep_wip">🚀</span> Min |
| <span class="spec">[abs <sup>element-wise unary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-unary)</span> | [📈](https://wpt.fyi/results/webnn/elementwise_unary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_unary.https.any.js) | <span class="x_s">✅</span> abs | <span class="ed_s">✅ Abs</span> | <span class="ep_wip">🚀</span> Abs |
| <span class="spec">[ceil <sup>element-wise unary</sup>](https://www.w3.org/TR/webnn/api-mlgraphbuilder-unary)</span> | [📈](https://wpt.fyi/results/webnn/elementwise_unary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_unary.https.any.js) | <span class="x_s">✅</span> ceiling | <span class="ed_s">✅ Ceil</span> | <span class="ep_s">✅</span> Ceil |
| <span class="spec">[floor <sup>element-wise unary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-unary)</span> |[📈](https://wpt.fyi/results/webnn/elementwise_unary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_unary.https.any.js) | <span class="x_s">✅</span> floor | <span class="ed_s">✅ Floor</span> | <span class="ep_s">✅</span> Floor |
| <span class="spec">[neg <sup>element-wise unary</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-unary)</span> | [📈](https://wpt.fyi/results/webnn/elementwise_unary.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elementwise_unary.https.any.js) | <span class="x_s">✅</span> negate | <span class="ed_s">✅ Neg</span> | <span class="ep_wip">🚀</span> Neg |
| <span class="spec">[elu](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-elu)</span> | [📈](https://wpt.fyi/results/webnn/elu.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/elu.https.any.js) | <span class="x_s">✅</span> elu | <span class="ed_s">✅</span> Elu | <span class="ep_wip">🚀</span> Elu |
| <span class="spec">[gemm](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-gemm)</span> | [📈](https://wpt.fyi/results/webnn/gemm.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/gemm.https.any.js) | <span class="x_s">✅</span> fully_connected | <span class="ed_s">✅</span> FullyConnected | <span class="ep_s">✅</span> Gemm |
| <span class="spec">[hardSwish](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-hard-swish)</span> | [📈](https://wpt.fyi/results/webnn/hard_swish.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/hard_swish.https.any.js) | <span class="x_s">✅</span> hardswish | <span class="ed_s">✅</span> HardSwish | <span class="ep_wip">🚀</span> HardSwish |
| <span class="spec">[leakyRelu](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-leakyrelu)</span> | [📈](https://wpt.fyi/results/webnn/leaky_relu.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/leaky_relu.https.any.js) | <span class="x_s">✅</span> leaky_relu | <span class="ed_s">✅</span> LeakyRelu | <span class="ep_s">✅</span> LeakyRelu |
| <span class="spec">[pad](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-pad)</span> | [📈](https://wpt.fyi/results/webnn/pad.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/pad.https.any.js) | <span class="x_s">✅</span> static_constant_pad | <span class="ed_s">✅</span> Pad | <span class="ep_wip">🚀</span> Pad |
| <span class="spec">[averagePool2d <sup>pooling</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-pool2d)</span> | [📈](https://wpt.fyi/results/webnn/pooling.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/pooling.https.any.js) | <span class="x_s">✅</span> average_pooling_2d | <span class="ed_s">✅</span> AveragePool2d | <span class="ep_s">✅</span> GlobalAveragePool |
| ^^ | ^^ | ^^ | <span class="ed_s">✅</span> Mean | <span class="ep_s">✅</span> AveragePool |
| <span class="spec">[maxPool2d <sup>pooling</sup>](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-pool2d)</span> | [📈](https://wpt.fyi/results/webnn/pooling.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/pooling.https.any.js) | <span class="x_s">✅</span> max_pooling_2d | <span class="ed_s">✅</span> MaxPool2d | <span class="ep_s">✅</span> GlobalMaxPool |
| ^^ | ^^ | ^^ | ^^ | <span class="ep_s">✅</span> MaxPool |
| <span class="spec">[prelu](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-prelu)</span> | [📈](https://wpt.fyi/results/webnn/prelu.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/prelu.https.any.js) | <span class="x_s">✅</span> prelu | <span class="ed_s">✅</span> Prelu | <span class="ep_wip">🚀</span> Prelu |
| <span class="spec">[relu](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-relu)</span> | [📈](https://wpt.fyi/results/webnn/relu.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/relu.https.any.js) | <span class="x_s">✅</span> clamp | <span class="ed_s">✅</span> Relu | <span class="ep_s">✅</span> Relu |
| <span class="spec">[resample2d](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-resample2d)</span> | <span class="wpt_wip">🚀🚀</span> | <span class="x_s">✅</span> static_resize_bilinear_2d | <span class="ed_s">✅</span> ResizeBilinear | <span class="ep_s">✅</span> Resize |
| <span class="spec">[reshape](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-reshape)</span> | [📈](https://wpt.fyi/results/webnn/reshape.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/reshape.https.any.js) | <span class="x_s">✅</span> static_reshape | <span class="ed_s">✅</span> Reshape | <span class="ep_s">✅</span> Reshape |
| <span class="spec">[sigmoid](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-sigmoid)</span> | [📈](https://wpt.fyi/results/webnn/sigmoid.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/sigmoid.https.any.js) | <span class="x_s">✅</span> sigmoid | <span class="ed_s">✅</span> Logistic | <span class="ep_s">✅</span> Sigmoid |
| <br><br><span class="spec">[split](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-split)</span> | [📈](https://wpt.fyi/results/webnn/split.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/split.https.any.js) | <span class="x_s">✅</span> even_split2 | <br><br><span class="ed_s">✅</span> Split | <br><br><span class="ep_s">✅</span> Split |
| ^^ | ^^ | <span class="x_s">✅</span> even_split3 | ^^ | ^^ |
| ^^ | ^^ | <span class="x_s">✅</span> even_split4 | ^^ | ^^ |
| ^^ | ^^ | <span class="x_s">✅</span> static_slice (uneven split) | ^^ | ^^ |
| <span class="spec">[slice](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-slice)</span> | [📈](https://wpt.fyi/results/webnn/slice.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/slice.https.any.js) | <span class="x_s">✅</span> static_slice | <span class="ed_s">✅</span> Slice | <span class="ep_s">✅</span> Slice |
| ^^ | ^^ | ^^ | <span class="ed_s">✅</span> StridedSlice | ^^ |
| <span class="spec">[softmax](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-softmax)</span> | [📈](https://wpt.fyi/results/webnn/softmax.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/softmax.https.any.js) | <span class="x_s">✅</span> softmax | <span class="ed_s">✅</span> Softmax | <span class="ep_s">✅</span> Softmax | 
| <span class="spec">[transpose](https://www.w3.org/TR/webnn/#api-mlgraphbuilder-transpose)</span> | [📈](https://wpt.fyi/results/webnn/transpose.https.any.html?label=master&label=experimental) [<span class="wpt_s">🧪</span>](https://github.com/web-platform-tests/wpt/blob/master/webnn/transpose.https.any.js) | <span class="x_s">✅</span> static_transpose | <span class="ed_s">✅</span> Transpose | <span class="ep_s">✅</span> Transpose |
| {: #spec_total } {: class="title"} | {: #wpt_total } {: class="title"} | {: #x_total } {: class="title"} | {: #ed_total } {: class="title"} | {: #ep_total } {: class="title"} |

<div class="impl_status">
    <div class="title">XNNPack/CPU backend</div>
    <div class="title">TensorFlow Lite External Delegate</div>
    <div class="title">ONNX Runtime Execution Provider</div>
    <div>
        <div>✅ Supported (<span id="supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="partlyimplemented"></span>)</div>
        <div>🔍 Code Review (<span id="codereview"></span>)</div>
        <div>🚀 Work in Progress (<span id="workinprogress"></span>)</div>
        <div>❌ Not Support</div>
    </div>
        <div>
        <div>✅ Supported (<span id="ed_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="ed_partlyimplemented"></span>)</div>
        <div>🔍 Code Review (<span id="ed_codereview"></span>)</div>
        <div>🚀 Work in Progress (<span id="ed_workinprogress"></span>)</div>
        <div>❌ Not Support</div>
    </div>
    <div>
        <div>✅ Supported (<span id="ep_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="ep_partlyimplemented"></span>)</div>
        <div>🔍 Code Review (<span id="ep_codereview"></span>)</div>
        <div>🚀 Work in Progress (<span id="ep_workinprogress"></span>)</div>
        <div>❌ Not Support</div>
    </div>
</div> 

<sup>[1]</sup> XNNPack node definition in [`xnn_define_*`](https://github.com/google/XNNPACK/blob/master/include/xnnpack.h)<br>
<sup>[2]</sup> TensorFlow Lite built-in operators [`kTfLiteBuiltin*`](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/lite/delegates/xnnpack/xnnpack_delegate.cc)<br>
<sup>[3]</sup> ONNX [`Operator Schemas`](https://github.com/onnx/onnx/blob/main/docs/Operators.md) and [`WebNN EP Helper`](https://github.com/microsoft/onnxruntime/blob/main/onnxruntime/core/providers/webnn/builders/helper.h)<br>
<sup>[4]</sup> Enabled in [Google Chrome Dev 115](https://www.google.com/chrome/dev/) and [Microsoft Edge Canary 115](https://www.microsoftedgeinsider.com/en-us/download/canary) channels

<script>
  const count = () => {
    document.querySelector('#spec_total').innerHTML = document.querySelectorAll('.spec').length;
    document.querySelector('#wpt_total').innerHTML = document.querySelectorAll('.wpt_s').length;

    let x_s = document.querySelectorAll('.x_s').length;
    let x_pi = document.querySelectorAll('.x_pi').length;
    let x_cr = document.querySelectorAll('.x_cr').length;
    let x_wip = document.querySelectorAll('.x_wip').length;
    let x_total = x_s + x_pi + x_cr + x_wip;
    document.querySelector('#x_total').innerHTML = x_total;

    document.querySelector('#supported').innerHTML = x_s;
    document.querySelector('#partlyimplemented').innerHTML = x_pi;
    document.querySelector('#codereview').innerHTML = x_cr;
    document.querySelector('#workinprogress').innerHTML = x_wip;
 
    let ed_s = document.querySelectorAll('.ed_s').length;
    let ed_pi = document.querySelectorAll('.ed_pi').length;
    let ed_cr = document.querySelectorAll('.ed_cr').length;
    let ed_wip = document.querySelectorAll('.ed_wip').length;
    let ed_total = ed_s + ed_pi + ed_cr + ed_wip;
    document.querySelector('#ed_total').innerHTML = ed_total;
    
    document.querySelector('#ed_supported').innerHTML = ed_s;
    document.querySelector('#ed_partlyimplemented').innerHTML = ed_pi;
    document.querySelector('#ed_codereview').innerHTML = ed_cr;
    document.querySelector('#ed_workinprogress').innerHTML = ed_wip;

    let ep_s = document.querySelectorAll('.ep_s').length;
    let ep_pi = document.querySelectorAll('.ep_pi').length;
    let ep_cr = document.querySelectorAll('.ep_cr').length;
    let ep_wip = document.querySelectorAll('.ep_wip').length;
    let ep_total = ep_s + ep_pi + ep_cr + ep_wip;
    document.querySelector('#ep_total').innerHTML = ep_total;
    
    document.querySelector('#ep_supported').innerHTML = ep_s;
    document.querySelector('#ep_partlyimplemented').innerHTML = ep_pi;
    document.querySelector('#ep_codereview').innerHTML = ep_cr;
    document.querySelector('#ep_workinprogress').innerHTML = ep_wip;
  }
 document.addEventListener('DOMContentLoaded', count, false);
</script>
