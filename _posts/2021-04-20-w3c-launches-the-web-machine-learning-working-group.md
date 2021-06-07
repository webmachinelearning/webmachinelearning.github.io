---
layout: post
title:  "W3C Launches the Web Machine Learning Working Group"
date:   2021-04-20 18:00:00 +0800
author: Dominique Hazaël-Massieux
avatar: https://avatars.githubusercontent.com/u/216410?v=4
categories: blog
toc: true
---

## Introduction

Machine Learning (ML) is a branch of Artificial Intelligence. A subfield of ML called Deep Learning with its various neural network architectures enables new compelling user experiences for web applications. [Use cases](https://webmachinelearning.github.io/webnn/#usecases) range from improved video conferencing to accessibility-improving features, with potential improved privacy over cloud-based solutions. Enabling these use cases and more is the focus of the newly launched [Web Machine Learning Working Group](https://www.w3.org/groups/wg/webmachinelearning").

![WebNN Logo]({{ '/assets/images/webml-logo-sm.png' | relative_url }})

## Progress

While some of these use cases can be implemented in-device in a constrained manner with existing Web APIs (e.g. WebGL graphics API or in the future [WebGPU](https://gpuweb.github.io/gpuweb/), the lack of access to platform capabilities such as dedicated ML hardware accelerators and native instructions constraint the scope of experiences and leads to inefficient implementations on modern hardware.

<!-- more -->

With these design goals in mind, a [W3C Community Group](https://www.w3.org/community/webmachinelearning/) started incubating work in 2018 for a possible Web Neural Network API, in response to encouraging feedback from a [TPAC breakout session](https://www.w3.org/2018/10/24-webmachinelearning-minutes.html). Starting October 2018, this Community Group identified key use cases working with diverse participants including major browser vendors, key ML JS frameworks, interested hardware vendors, and web developers. After identification of the key use cases, the group decomposed the key use cases into requirements and started drafting the [Web Neural Network API specification](https://webmachinelearning.github.io/webnn) in mid-2019. The aim of this use case-driven design process was to put user needs first.

### Quotes 

> “Having access to the native ML accelerators, machine learning frameworks such as TensorFlow.js can greatly improve model execution efficiency and truly democratize ML for web developers.”
>
> – Ping Yu, TLM for [TensorFlow.js](https://www.tensorflow.org/js") at Google

> “The [early empirical results from the Web Neural Network API implementations](https://www.w3.org/2020/06/machine-learning-workshop/talks/access_purpose_built_ml_hardware_with_web_neural_network_api.html#slide-10) demonstrate tremendous power &amp; performance improvements of the Web AI workloads. Through access to the full native AI capabilities of the modern heterogeneous hardware, the Web Neural Network API enables a whole new transformative class of intelligent user experiences on the Open Web Platform across a variety of hardware, software, and device types.” 
> 
> &#8211; Ningxin Hu, Principal Engineer, Web Platform Engineering at Intel

W3C organized a [workshop on Web and Machine Learning](https://www.w3.org/2020/06/machine-learning-workshop) over the course of August and September 2020. This workshop brought together web platform and machine learning practitioners to survey the broader intersection of Web technologies and Machine Learning, and one of the [conclusions of the Workshop](https://www.w3.org/2020/06/machine-learning-workshop/report.html) was to propose that [a new W3C Working Group should be formed](https://lists.w3.org/Archives/Public/public-new-work/2021Feb/0007.html) to standardize the Web Neural Network API, graduating from its incubation stage. As of 2021, the Community Group continues its incubation function working in parallel with the Working Group, similarly to e.g. W3C’s WebAssembly and WebGPU efforts.

> “The Web Neural Network API is a very important step toward the future of the Intelligent Web where AI is infused into the user&#8217;s daily web experiences. With the current advances and the pace of innovations in the AI hardware landscape, it&#8217;ll help connect those experiences from the clouds and make them personal to the users through seamless native hardware performance on the edge devices across the entire web. That&#8217;s the future worth dreaming about!”
> 
> &#8211; [Chai Chaoweeraprasit](https://www.w3.org/2020/06/machine-learning-workshop/talks/accelerated_graphics_and_compute_api_for_machine_learning_directml.html), Principal Engineering Lead, Machine Learning and Compute Platform at Microsoft

The [Web Machine Learning Working Group](https://www.w3.org/groups/wg/webmachinelearning) plans to publish the First Public Working Draft of the Web Neural Network API during the first half of 2021 and welcomes new participants from the diverse W3C community to take part in helping identify new use cases, documenting ethical risks and their mitigations, contributing to technical work, conducting wide reviews in privacy, security, accessibility, and other important areas to ensure the perspectives of the diverse web community are heard. &#8211; which given some of the ethical impact of Machine Learning algorithms will be particularly critical to the work of the group. Join us!

We would like to thank all the W3C Community Group and W3C workshop participants for their contributions that have helped shape this work, and W3C for providing a venue to advance this cross-industry effort toward wide adoption.

*This post is co-authored by Anssi Kostiainen (Working Group Chair), Ningxin Hu and Chai Chaoweeraprasit (Web Neural Network API Editors), and Ping Yu (TensorFlow.js Core team).*

*Source: [W3C Launches the Web Machine Learning Working Group](https://www.w3.org/blog/2021/04/w3c-launches-the-web-machine-learning-working-group/)*



			


