---
layout: post
title:  "WebNN-Native Build and Run"
date:   2021-03-25 18:00:00 +0800
author: Ningxin, Junwei, Bruce and Mingming
avatar: https://avatars.githubusercontent.com/u/1531742?v=4
categories: doc
toc: true
---

WebNN-native is a native implementation of the [Web Neural Network API](https://webmachinelearning.github.io/webnn/).

It provides several building blocks:

 - **WebNN C/C++ headers** that applications and other building blocks use.
   - The `webnn.h` that is an one-to-one mapping with the WebNN IDL.
   - A C++ wrapper for the `webnn.h`
 - **Backend implementations** that use platforms' ML APIs:
   - **DirectML** on Windows 10
   - **OpenVINO** on Windows 10 and Linux
   - **oneDNN** on Windows 10 and Linux
   - **XNNPACK** on Windows 10 and Linux
   - _Other backends are to be added_

<!-- more -->

WebNN-native uses the code of other open source projects:

 * The code generator and infrastructure code of [Dawn](https://dawn.googlesource.com/dawn/) project.
 * The DirectMLX and device wrapper of [DirectML](https://github.com/microsoft/DirectML) project.
 * The [XNNPACK](https://github.com/google/XNNPACK)

## Build and Run

### Install `depot_tools`

WebNN-native uses the Chromium build system and dependency management so you need to [install depot_tools] and add it to the PATH.

[install depot_tools]: http://commondatastorage.googleapis.com/chrome-infra-docs/flat/depot_tools/docs/html/depot_tools_tutorial.html#_setting_up

**Notes**:
 * On Windows, you'll need to set the environment variable `DEPOT_TOOLS_WIN_TOOLCHAIN=0`. This tells depot_tools to use your locally installed version of Visual Studio (by default, depot_tools will try to download a Google-internal version).

### Get the code

Get the source code as follows:

```sh
# Clone the repo as "webnn-native"
> git clone https://github.com/webmachinelearning/webnn-native.git webnn-native && cd webnn-native

# Bootstrap the gclient configuration
> cp scripts/standalone.gclient .gclient

# Fetch external dependencies and toolchains with gclient
> gclient sync
```

### Setting up the build

Generate build files using `gn args out/Debug` or `gn args out/Release`.

A text editor will appear asking build options, the most common option is `is_debug=true/false`; otherwise `gn args out/Release --list` shows all the possible options.

To build with DirectML backend, set build option `webnn_enable_dml=true`.

To build with OpenVINO backend, set build option `webnn_enable_openvino=true`.

To build with oneDNN backend, set build option `webnn_enable_onednn=true`.

To build with XNNPACK backend, set build option `webnn_enable_xnnpack=true`.

### Build

Then use `ninja -C out/Release` or `ninja -C out/Debug` to build WebNN-native.

**Notes**
 * To build with XNNPACK backend, please build XNNPACK first, e.g. by [`XNNPACK/scripts/build-local.sh`](https://github.com/google/XNNPACK/blob/master/scripts/build-local.sh).

### Run tests

Run unit tests, for example `./out/Release/webnn_unittests`.

Run end2end tests, for example `./out/Release/webnn_end2end_tests`.

**Notes**:
 * For OpenVINO backend, please [install 2021.2 version](https://docs.openvinotoolkit.org/2021.2/openvino_docs_install_guides_installing_openvino_linux.html#install-openvino) and [set the environment variables](https://docs.openvinotoolkit.org/2021.2/openvino_docs_install_guides_installing_openvino_linux.html#set-the-environment-variables) before running the end2end tests.
 * For oneDNN backend on Linux, please set the `LD_LIBRARY_PATH` environment variable to the out folder before running the end2end tests, e.g. `LD_LIBRARY_PATH=./out/Release ./out/Release/webnn_end2end_tests`.

## License

Apache 2.0 Public License.
