# Contributing to Web Machine Learning website

First of all, thank you very much for your interest in contributing to Web Machine Learning website! We're really happy to accept contributions from everyone, whether you're a browser engineer, a spec writer or a web developer.

## WebNN Implementation Status

This repository contains raw data from the [WebNN Implementation Status](https://webmachinelearning.github.io/webnn-status/) tables. If you are interested in updating or adding to the WebNN Implementation Status data on the site, please edit the [webnn_status.json](./assets/json/webnn_status.json) file.

The WebNN API [browser compat data (BCD)](https://github.com/search?q=repo%3Amdn%2Fbrowser-compat-data+webnn&type=code) is the upstream and we will keep it up to date as a first priority. The [webnn_status.json](./assets/json/webnn_status.json) adds the following domain-specific data on top of the [WebNN API BCD](https://github.com/search?q=repo%3Amdn%2Fbrowser-compat-data+webnn&type=code) baseline data:

- WebNN ops mapping to native backends
- WebNN WPT test and test result links
- WebNN JavaScript ML Frameworks integration status

### WebNN Implementation Status Data

The [webnn_status.json](./assets/json/webnn_status.json) is the data source for the [WebNN Implementation Status](https://webmachinelearning.github.io/webnn-status/) page. By contributing updates to this file on GitHub you can help keep the implementation status page up to date. An example entry for the [`argMax`](https://www.w3.org/TR/webnn/#dom-mlgraphbuilder-argmax) op looks like the following:

```
    {
      "op": "argMax",
      "op_id": "argminmax",
      "version": "",
      "wpt": "arg_min_max",
      "wpt_progress": 4,
      "xnnpack_op": [
        ""
      ],
      "xnnpack_progress": 2,
      "xnnpack_chromium_version_added": "",
      "dml_op": [
        "REDUCE_FUNCTION_ARGMAX"
      ],
      "dml_progress": 4,
      "dml_chromium_version_added": "M122",
      "mlservice_op": [
        ""
      ],
      "mlservice_progress": 2,
      "mlservice_chromium_version_added": "",
      "tflite_op": [
        ""
      ],
      "tflite_progress": 2,
      "tflite_version_added": "",
      "ort_op": [
        "ArgMax"
      ],
      "ort_progress": 4,
      "ort_version_added": "main",
      "notes": ""
    }
```    

### Supported Changes

Currently the following feature information can be modified for WebNN XNNPACK, DirectML and MLService backends:

* **op** - Operation name defined in [Web Neural Network API](https://www.w3.org/TR/webnn/) spec
* **op_id** - Operation name defined in anchor link in the spec
* **wpt** - The WebNN test cases id used in [Web Platform Tests](https://github.com/web-platform-tests/wpt/tree/master/webnn) and [WPT dashboard](https://wpt.fyi/)
* **[*]_op** - The operation list of native ML libraries or the JavaScript ML frameworks that map to WebNN API
* **[*]_version_added** - The Chromium or the JavaScript ML framework version where support for the feature was added
* **[*]_progress**
    * **1** - Not Implemented / Not Supported
    * **2** - In Planning
    * **3** - Work in Progress
    * **4** - Implemented / Supported

## License

The data in this repository is available for use under the [W3C Software and Document license](https://www.w3.org/Consortium/Legal/copyright-software).