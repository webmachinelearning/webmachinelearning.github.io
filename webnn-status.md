---
layout: page
title: Implementation Status of WebNN Operations
permalink: /webnn-status/
---

<style>
.post img {
 height: 24px;
 margin: 4px 0;
 transform: none;
 display: inline-block;
 min-width: 24px;
}

.post .onnxrt img {
 width: 80px;
}

.post .tflite img {
 width: 102px;
}

.post table {
  font-size: 0.8rem;
}

.post table tr td {
  text-align: left;
}

.post table tr td:nth-child(1), 
.post table tr td:nth-child(2),
.post table tr td:nth-child(4), 
.post table tr td:nth-child(6),
.post table tr td:nth-child(8), 
.post table tr td:nth-child(10) {
  text-align: center;
}

.post table td {
  padding: 4px 6px;
  vertical-align: middle;
}

.post table th {
  padding: 6px 6px;
}

.impl_status {
   text-align: center;
   display: grid; 
   grid-template-columns: 1fr 1fr 1fr 1fr;
   gap: 0px;
   border: 1px solid #dfe2e5;
   padding: 12px;
   font-size: 0.9em;
}

.impl_status .title {
  font-size: 1rem;
  line-height: 1rem;
}
.post-content table th {
  font-weight: 400;
  font-size: 0.9rem;
  line-height: 0.9rem;
}

.post svg#w3 {
  transform: none;
  height: 36px;
  width: 72px;
}

sup {
  font-size: 0.7rem;
}

.impl_status .title {
  margin-bottom: 0.4rem;
}

.impl_status div {
  margin: 0 12px;
}
</style>

<table>
  <thead>
    <tr class="title">
      <th rowspan="3">
        <a href="https://www.w3.org/TR/webnn/">
          <svg id="w3" x="0px" y="0px" viewBox="0 0 357.5 287" style="enable-background:new 0 0 357.5 287;">
            <style type="text/css">
              .st0 {
                fill: #005A9C;
              }

              .st1 {
                fill: #221B0A;
              }
            </style>
            <g>
              <path class="st0" d="M118.4,76.6l24.2,82.4l24.2-82.4h17.5l-40.1,135.3h-1.7l-25.1-83.8l-25.1,83.8h-1.7L50.8,76.6h17.5L92.5,159
                    l16.4-55.5l-8-26.9L118.4,76.6L118.4,76.6z" />
              <path class="st0" d="M234.2,168.5c0,12.3-3.3,22.6-9.8,30.9c-6.5,8.3-15,12.5-25.3,12.5c-7.8,0-14.6-2.5-20.4-7.4
                    c-5.8-5-10.1-11.7-12.9-20.1l13.7-5.7c2,5.1,4.7,9.2,7.9,12.1c3.3,2.9,7.1,4.4,11.6,4.4c4.7,0,8.6-2.6,11.9-7.9
                    c3.2-5.2,4.8-11.5,4.8-18.9c0-8.1-1.7-14.4-5.2-18.9c-4-5.2-10.3-7.9-18.9-7.9h-6.7v-8l23.4-40.4h-28.2l-7.9,13.4h-5V76.6h65.1v8.2
                    l-24.7,42.6c8.7,2.8,15.3,7.9,19.7,15.2C232,149.9,234.2,158.6,234.2,168.5L234.2,168.5z" />
              <path class="st1"
                d="M302.2,75.9l2.8,17.3l-10.1,19.2c0,0-3.9-8.2-10.3-12.7c-5.4-3.8-8.9-4.6-14.4-3.5
                    c-7.1,1.5-15.1,9.9-18.6,20.3c-4.2,12.5-4.2,18.5-4.4,24c-0.2,8.9,1.2,14.1,1.2,14.1s-6.1-11.3-6-27.8c0-11.8,1.9-22.5,7.4-33.1
                    c4.8-9.3,11.9-14.9,18.3-15.5c6.6-0.7,11.7,2.5,15.7,5.9c4.2,3.6,8.5,11.4,8.5,11.4L302.2,75.9L302.2,75.9z" />
              <path class="st1" d="M303.4,173.6c0,0-4.4,7.9-7.2,11c-2.8,3.1-7.7,8.5-13.8,11.2c-6.1,2.7-9.3,3.2-15.4,2.6
                    c-6-0.6-11.7-4.1-13.6-5.5c-2-1.4-7-5.8-9.8-9.7c-2.9-4-7.3-12-7.3-12s2.5,8,4,11.4c0.9,2,3.6,8,7.5,13.2
                    c3.6,4.9,10.7,13.3,21.4,15.1c10.7,1.9,18.1-2.9,19.9-4.1c1.8-1.2,5.7-4.4,8.1-7c2.5-2.7,4.9-6.2,6.3-8.2c1-1.5,2.6-4.6,2.6-4.6
                    L303.4,173.6L303.4,173.6z" />
            </g>
          </svg>
          <br />WebNN Spec
        </a>
      </th>
      <th rowspan="3">Web Platform<br />Tests</th>
      <th colspan="4">
        Chromium Implementation
      </th>
      <th colspan="4">JavaScript ML Frameworks Integration</th>
    </tr>
    <tr class="title">
      <th colspan="2"><img src="https://wpt.fyi/static/win.svg"> <img
          src="https://wpt.fyi/static/linux.svg"><br />XNNPack/CPU
        backend
        <sup>1</sup>
      </th>
      <th colspan="2"><img src="https://wpt.fyi/static/win.svg"><br />DirectML/GPU backend <sup>2</sup>
      </th>
      <th colspan="2"><img
          src="https://www.gstatic.com/devrel-devsite/prod/v8ec4d0a037302c47ae529ad4e3f06c9e782b3a31a381294b5a70403547dc6b12/tensorflow/images/lockup.svg">
        Lite for TF.js<br />External Delegate <sup>3</sup></th>
      <th colspan="2"><img src="https://onnxruntime.ai/images/svg/ONNX-Runtime-logo.svg" /><br />Execution Provider
        <sup>4</sup>
      </th>
    </tr>
    <tr class="title">
      <th>Operations
      </th>
      <th>
        <img src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/chrome-dev/chrome-dev_128x128.png" />
        <img
          src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/edge-canary/edge-canary_128x128.png" /> <sup>5</sup>
      </th>
      <th>Operations</th>
      <th>
        <img src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/chrome-dev/chrome-dev_128x128.png" />
        <img
          src="https://raw.githubusercontent.com/alrra/browser-logos/main/src/edge-canary/edge-canary_128x128.png" /> <sup>5</sup>
      </th>
      <th>Operations
      </th>
      <th>Delegate Version
      </th>
      <th>Operations
      </th>
      <th>EP Version
      </th>
    </tr>
  </thead>
  <tbody id="ops"></tbody>
</table>

<div class="impl_status">
    <div class="title">XNNPack/CPU backend</div>
    <div class="title">DirectML/GPU backend</div>
    <div class="title">TensorFlow.js/TFLite<br/>External Delegate</div>
    <div class="title">ONNX Runtime Web<br/>Execution Provider</div>
    <div>
        <div>✅ Supported (<span id="x_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="x_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="x_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
    <div>
        <div>✅ Supported (<span id="dml_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="dml_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="dml_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
    <div>
        <div>✅ Supported (<span id="ed_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="ed_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="ed_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
    <div>
        <div>✅ Supported (<span id="ep_supported"></span>)</div>
        <div>⏳ Partly Implemented (<span id="ep_partlyimplemented"></span>)</div>
        <div>🚀 Work in Progress (<span id="ep_workinprogress"></span>)</div>
        <div>❌ Not Supported</div>
    </div>
</div> 

The total number of WebNN v1 ops is 60. This table currently lists ops that are implemented or WIP by multiple backends.

<sup>[1]</sup> XNNPack node definition in [`xnn_define_*`](https://github.com/google/XNNPACK/blob/master/include/xnnpack.h)<br/>
<sup>[2]</sup> [DirectML](https://learn.microsoft.com/en-us/windows/win32/api/_directml/) API<br/>
<sup>[3]</sup> TensorFlow Lite built-in operators [`kTfLiteBuiltin*`](https://github.com/tensorflow/tensorflow/blob/master/tensorflow/lite/delegates/xnnpack/xnnpack_delegate.cc)<br/>
<sup>[4]</sup> ONNX [`Operator Schemas`](https://github.com/onnx/onnx/blob/main/docs/Operators.md) and [`WebNN EP Helper`](https://github.com/microsoft/onnxruntime/blob/main/onnxruntime/core/providers/webnn/builders/helper.h)<br/>
<sup>[5]</sup> Currently enabled in [Google Chrome Dev](https://www.google.com/chrome/dev/) and [Microsoft Edge Canary](https://www.microsoftedgeinsider.com/en-us/download/canary) channels with #enable-experimental-web-platform-features flag.

<script>
  const qS = (selector) => {
    return document.querySelector(selector);
  }
  
  const qSA = (selector) => {
    return document.querySelectorAll(selector);
  }
  
  const init = () => {
    let ops = document.querySelector('#ops');
    fetch("https://webmachinelearning.github.io/assets/json/webnn_status.json")
      .then(response => response.json())
      .then(data => {
        let impl_status = data.impl_status;

        let oplist = '';

        for (let s of impl_status) {

          let spec = `<td class="spec"><a href="https://www.w3.org/TR/webnn/#api-mlgraphbuilder-${s.op_id}">${s.op}</a></td>`

          let wpt = '';
          if (s.wpt_progress === 4) {
            wpt = `<td class="wpt_s">
                      <a href="https://wpt.fyi/results/webnn/${s.wpt}.https.any.html?label=master&amp;label=experimental">📈</a> 
                      <a href="https://github.com/web-platform-tests/wpt/blob/master/webnn/${s.wpt}.https.any.js">🧪</a></td>`
          } 
          if (s.wpt_progress === 3) {
            wpt = `<td class="wpt_wip">🚀🚀</td>`
          }

          let xnnpack = '';
          if (s.xnnpack_op.toString().trim() === "") {
            xnnpack = `<td></td><td>${s.xnnpack_chromium_version_added}</td>`;
          } else if (s.xnnpack_progress === 4) {
            let xnnpack_ops = '';
            if (s.xnnpack_op.length > 1) {
              for (let o of s.xnnpack_op) {
                xnnpack_ops = `✅ ${o} <br/>`;
                xnnpack += xnnpack_ops;
              }
            } else if (s.xnnpack_op.length === 1) {
              xnnpack = '✅ ' + s.xnnpack_op;
            } else {
              xnnpack = ``
            }
            xnnpack = `<td class="x_s">${xnnpack}</td><td>${s.xnnpack_chromium_version_added}</td>`;
          } else if (s.xnnpack_progress === 3) {
            let xnnpack_ops = '';
            if (s.xnnpack_op.length > 1) {
              for (let o of s.xnnpack_op) {
                xnnpack_ops = `🚀 ${o} <br/>`;
                xnnpack += xnnpack_ops;
              }
            } else if (s.xnnpack_op.length === 1) {
              xnnpack = '🚀 ' + s.xnnpack_op;
            } else {
              xnnpack = ``
            }
            xnnpack = `<td class="x_wip">${xnnpack}</td><td>${s.xnnpack_chromium_version_added}</td>`;
          } else if (s.xnnpack_progress === 2) {
            let xnnpack_ops = '';
            if (s.xnnpack_op.length > 1) {
              for (let o of s.xnnpack_op) {
                xnnpack_ops = `📅 ${o} <br/>`;
                xnnpack += xnnpack_ops;
              }
            } else if (s.xnnpack_op.length === 1) {
              xnnpack = '📅 ' + s.xnnpack_op;
            } else {
              xnnpack = ``
            }
            xnnpack = `<td class="x_plan">${xnnpack}</td><td>${s.xnnpack_chromium_version_added}</td>`;
          } else {
            xnnpack = `<td></td><td>${s.xnnpack_chromium_version_added}</td>`;
          }

          let dml = '';
          if (s.dml_op.toString().trim() === "") {
            dml = `<td></td><td>${s.dml_chromium_version_added}</td>`;
          } else if (s.dml_progress === 4) {
            let dml_ops = '';
            if (s.dml_op.length > 1) {
              for (let o of s.dml_op) {
                dml_ops = `✅ ${o} <br/>`;
                dml += dml_ops;
              }
            } else if (s.dml_op.length === 1) {
              dml = '✅ ' + s.dml_op;
            } else {
              dml = ``
            }
            dml = `<td class="dml_s">${dml}</td><td>${s.dml_chromium_version_added}</td>`;
          } else if (s.dml_progress === 3) {
            let dml_ops = '';
            if (s.dml_op.length > 1) {
              for (let o of s.dml_op) {
                dml_ops = `🚀 ${o} <br/>`;
                dml += dml_ops;
              }
            } else if (s.dml_op.length === 1) {
              dml = '🚀 ' + s.dml_op;
            } else {
              dml = ``
            }
            dml = `<td class="dml_wip">${dml}</td><td>${s.dml_chromium_version_added}</td>`;
          } else if (s.dml_progress === 2) {
            let dml_ops = '';
            if (s.dml_op.length > 1) {
              for (let o of s.dml_op) {
                dml_ops = `📅 ${o} <br/>`;
                dml += dml_ops;
              }
            } else if (s.dml_op.length === 1) {
              dml = '📅 ' + s.dml_op;
            } else {
              dml = ``
            }
            dml = `<td class="dml_plan">${dml}</td><td>${s.dml_chromium_version_added}</td>`;
          } else {
            dml = `<td></td><td>${s.dml_chromium_version_added}</td>`;
          }

          let tflite = '';
          if (s.tflite_op.toString().trim() === "") {
            tflite = `<td></td><td>${s.tflite_version_added}</td>`;
          } else if (s.tflite_progress === 4) {
            let tflite_ops = '';
            if (s.tflite_op.length > 1) {
              for (let o of s.tflite_op) {
                tflite_ops = `✅ ${o} <br/>`;
                tflite += tflite_ops;
              }
            } else if (s.tflite_op.length === 1) {
              tflite = '✅ ' + s.tflite_op;
            } else {
              tflite = ``
            }
            tflite = `<td class="ed_s">${tflite}</td><td>${s.tflite_version_added}</td>`;
          } else if (s.tflite_progress === 3) {
            let tflite_ops = '';
            if (s.tflite_op.length > 1) {
              for (let o of s.tflite_op) {
                tflite_ops = `🚀 ${o} <br/>`;
                tflite += tflite_ops;
              }
            } else if (s.tflite_op.length === 1) {
              tflite = '🚀 ' + s.tflite_op;
            } else {
              tflite = ``
            }
            tflite = `<td class="ed_wip">${tflite}</td><td>${s.tflite_version_added}</td>`;
          } else if (s.tflite_progress === 2) {
            let tflite_ops = '';
            if (s.tflite_op.length > 1) {
              for (let o of s.tflite_op) {
                tflite_ops = `📅 ${o} <br/>`;
                tflite += tflite_ops;
              }
            } else if (s.tflite_op.length === 1) {
              tflite = '📅 ' + s.tflite_op;
            } else {
              tflite = ``
            }
            tflite = `<td class="ed_plan">${tflite}</td><td>${s.tflite_version_added}</td>`;
          } else {
            tflite = `<td></td><td>${s.tflite_version_added}</td>`;
          }

          let ort = '';
          if (s.ort_op.toString().trim() === "") {
            ort = `<td></td><td>${s.ort_version_added}</td>`;
          } else if (s.ort_progress === 4) {
            let ort_ops = '';
            if (s.ort_op.length > 1) {
              for (let o of s.ort_op) {
                ort_ops = `✅ ${o} <br/>`;
                ort += ort_ops;
              }
            } else if (s.ort_op.length === 1) {
              ort = '✅ ' + s.ort_op;
            } else {
              ort = ``
            }
            ort = `<td class="ep_s">${ort}</td><td>${s.ort_version_added}</td>`;
          } else if (s.ort_progress === 3) {
            let ort_ops = '';
            if (s.ort_op.length > 1) {
              for (let o of s.ort_op) {
                ort_ops = `🚀 ${o} <br/>`;
                ort += ort_ops;
              }
            } else if (s.ort_op.length === 1) {
              ort = '🚀 ' + s.ort_op;
            } else {
              ort = ``
            }
            ort = `<td class="ep_wip">${ort}</td><td>${s.ort_version_added}</td>`;
          } else if (s.ort_progress === 2) {
            let ort_ops = '';
            if (s.ort_op.length > 1) {
              for (let o of s.ort_op) {
                ort_ops = `📅 ${o} <br/>`;
                ort += ort_ops;
              }
            } else if (s.ort_op.length === 1) {
              ort = '📅 ' + s.ort_op;
            } else {
              ort = ``
            }
            ort = `<td class="ep_plan">${ort}</td><td>${s.ort_version_added}</td>`;
          } else {
            ort = `<td></td><td>${s.ort_version_added}</td>`;
          }

          oplist += `
              <tr>
                ${spec}
                ${wpt}
                ${xnnpack}
                ${dml}
                ${tflite}
                ${ort}
              </tr>
          `;
        }

        oplist = oplist + `
          <tr>
            <th id="spec_total"></th>
            <th id="wpt_total"></th>
            <th id="x_total" colspan="2"></th>
            <th id="dml_total" colspan="2"></th>
            <th id="ed_total" colspan="2"></th>
            <th id="ep_total" colspan="2"></th>
          </tr>
        `;
        ops.innerHTML = oplist;
        count();
      })
      .catch(console.error);
  }

  const count = () => {
    let spec_v1_defined_total = 60; 

    let spec_s = qSA('.spec').length;
    let spec_percentage = (spec_s / spec_v1_defined_total * 100).toFixed(1) ;
    qS('#spec_total').innerHTML = `${spec_s} / ${spec_v1_defined_total}, ${spec_percentage}%`;
  
    let wpt_s = qSA('.wpt_s').length;
    let wpt_percentage = (wpt_s / spec_v1_defined_total * 100).toFixed(1) ;
    qS('#wpt_total').innerHTML = `${wpt_s} / ${spec_v1_defined_total}, ${wpt_percentage}%`;

    let x_s = qSA('.x_s').length;
    let x_pi = qSA('.x_pi').length;
    let x_wip = qSA('.x_wip').length;
    let x_percentage = (x_s / spec_v1_defined_total * 100).toFixed(1) ;
    qS('#x_total').innerHTML = `${x_s} / ${spec_v1_defined_total}, ${x_percentage}%`;
    qS('#x_supported').innerHTML = x_s;
    qS('#x_partlyimplemented').innerHTML = x_pi;
    qS('#x_workinprogress').innerHTML = x_wip;
        
    let dml_s = qSA('.dml_s').length;
    let dml_pi = qSA('.dml_pi').length;
    let dml_wip = qSA('.dml_wip').length;
    let dml_percentage = (dml_s / spec_v1_defined_total * 100).toFixed(1) ;
    qS('#dml_total').innerHTML = `${dml_s} / ${spec_v1_defined_total}, ${dml_percentage}%`;
    qS('#dml_supported').innerHTML = dml_s;
    qS('#dml_partlyimplemented').innerHTML = dml_pi;
    qS('#dml_workinprogress').innerHTML = dml_wip;
 
    let ed_s = qSA('.ed_s').length;
    let ed_pi = qSA('.ed_pi').length;
    let ed_wip = qSA('.ed_wip').length;
    let ed_percentage = (ed_s / spec_v1_defined_total * 100).toFixed(1) ;
    qS('#ed_total').innerHTML = `${ed_s} / ${spec_v1_defined_total}, ${ed_percentage}%`;
    qS('#ed_supported').innerHTML = ed_s;
    qS('#ed_partlyimplemented').innerHTML = ed_pi;
    qS('#ed_workinprogress').innerHTML = ed_wip;

    let ep_s = qSA('.ep_s').length;
    let ep_pi = qSA('.ep_pi').length;
    let ep_wip = qSA('.ep_wip').length;
    let ep_percentage = (ep_s / spec_v1_defined_total * 100).toFixed(1) ;
    qS('#ep_total').innerHTML = `${ep_s} / ${spec_v1_defined_total}, ${ep_percentage}%`;
    qS('#ep_supported').innerHTML = ep_s;
    qS('#ep_partlyimplemented').innerHTML = ep_pi;
    qS('#ep_workinprogress').innerHTML = ep_wip;
  }
 document.addEventListener('DOMContentLoaded', init, false);
</script>
