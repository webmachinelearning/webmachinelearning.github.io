# Contribution

First of all, thank you very much for your interest in contributing to Web Machine Learning website! We're really happy to accept contributions from everyone, whether you're a browser engineer, a spec writer or a web developer.

## WebNN Implementation Status

This repository contains raw data from the [WebNN Implementation Status](https://webmachinelearning.github.io/webnn-status/) tables. If you are interested in updating or adding to the WebNN Implementation Status data on the site, please edit the [webnn_status.json](./assets/json/webnn_status.json) file.

The WebNN API [browser compat data (BCD)](https://github.com/mdn/browser-compat-data/pull/22569) is the upstream and we will keep it up to date as a first priority. The [webnn_status.json](./assets/json/webnn_status.json) raw data is the enhancement of [WebNN API BCD](https://github.com/mdn/browser-compat-data/pull/22569).

- WebNN BCD data is unable to support WebNN mapped ops of each native backends
- WebNN BCD data doesn't include WPT tests and test results
- WebNN BCD data is unable to cover JavaScript ML Frameworks integration status

### WebNN Implementation Status Data

The [webnn_status.json](./assets/json/webnn_status.json) includes every feature found for [WebNN Implementation Status](https://webmachinelearning.github.io/webnn-status/). Maintaining this file on GitHub allows anyone to update or contribute to the support data on the site.

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

Currently the following feature information can be modified for WebNN XNNPACK, DirectML and MLService backends.

* **op** - Operation name defined in [Web Neural Network API](https://www.w3.org/TR/webnn/) spec
* **op_id** - Operation name defined in anchor link in the spec
* **wpt** - The WebNN test cases id used in [Web Platform Tests](https://github.com/web-platform-tests/wpt/tree/master/webnn) and [WPT dashboard](https://wpt.fyi/)
* **[*]_op** - The operation list of native ML libraries or the JavaScript ML frameworks that map to WebNN API
* **[*]_version_added** - The Chromium version or the JavaScript ML frameworks started to support this feature
* **[*]_progress**
    * **1** - Not Implemented / Not Supported
    * **2** - Work in Progress
    * **3** - Partial Implementation
    * **4** - Implemented / Supported

## License

The data in this repository is available for use under the [W3C Software and Document license](https://www.w3.org/Consortium/Legal/copyright-software).