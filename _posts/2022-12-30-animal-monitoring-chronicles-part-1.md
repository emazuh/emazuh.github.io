---
title: 'Animal Monitoring Chronicles (Part 1)'
date: 2022-12-30
permalink: /posts/2022/12/animal-monitoring-chronicles-part-1/
tags:
  - animal monitoring
  - computing for agriculutre
  - computing for wildlife monitoring
---

This blog is in progress
--------------------------

Low Resource Wildlife Monitoring
======================

With advances in remote sensing technology, there is excitment around new ways to tackle some of the sustainable developing goals. In this project, I focus on goals 2 (addressing food security) and 15 (protect and restore terrestrial ecosystems) while being mindful of goal 13 (combating climate change). Even though my end goal is for use cases in developing countries, this project uses a test bed in a farm in Eastern Washington that had limited access to cellular networks and limited access to power supply. In this blog post, a provide a brief summary of work I was doing in wildlife monitoring on the network edge and a statement of the current direction I am taking in the project.

## The Setup

The necessary conditions of interest to me for this project pertain to rugged environments. The main characteristics here are low computational resources (edge devices), limited access to communication networks and electric power constraints. I briefly discuss the location and devices used in the project in line with these constraints.

### Devices
For this project, I started with three edge devices - an android phone, a raspberry pi and a Microsoft [Azure Percept](https://azure.microsoft.com/en-us/products/azure-percept/#product-overview). I also had a standard camera trap in the setup to use as a comparison point with a standard device in the environmental monitoring community. The devices would be left out in the field so the setup needed to be water proof. I adapted a home depot bin with cut out view ports and the ports protected by camera lens. I also had holes from the side to serve as ventilation and passage entrance for wires. Cameras (phone, rpi camera, camera trap, percept camera) all have to be stable to take pictures/videos through the viewports, which I achieved by utilizing stiff portions of some equipments as support for flimsy ones (eg rubber band around camera trap to support phone). 
![image1](/files/edge-devices.jpg)

Due to the breadth of devices, I had to explore with many frameworks in the edge ecosystem (both from this project and from class projects). Some of the noteworthy ones include:
1. [Android studio with tensorflow lite](https://www.tensorflow.org/lite/android/quickstart) to setup a system for deploying sample model to an android app.
2. [ONNX](https://onnx.ai) framework for converting between models developed with different ML frameworks (eg between pytorch and tensorflow, between pytorch and [OpenVINO IR](https://docs.openvino.ai/latest/openvino_docs_MO_DG_IR_and_opsets.html) for intel hardware, etc).
3. Most of my model experimentation used [Pytorch](https://pytorch.org) (one of the most popular machine learning frameworks among ML academics)
4. Azure Percept [Development Kit](https://learn.microsoft.com/en-us/azure/azure-percept/azureeyemodule-overview) and other Azure ecosystem services such as Azure IoT Hub, Azure Cognitive Services, Azure ML Studio etc. The custom pytorch model deployment procedure for Azure Percept can be found [here](https://github.com/microsoft/azure-percept-advanced-development/blob/main/tutorials/pytorch-from-scratch-tutorial/pytorch-from-scratch-tutorial.md#pytorch-from-scratch-tutorial).
5. Azure blob storage for storing collected data from the devices.
6. [TVM](https://tvm.apache.org) for further optimizing model runtime for some supported devices ([android](https://tvm.apache.org/docs/how_to/deploy_models/deploy_model_on_android.html) and [rpi](https://tvm.apache.org/docs/how_to/deploy_models/deploy_model_on_rasp.html))
7. The baseline model I started the project with was [Tiny YOLOv3](https://pjreddie.com/darknet/yolo/). However, the use case care more about presence so future experiments have been based on [MobileNetV2](https://arxiv.org/pdf/1801.04381.pdf) and [EfficientNet-B0](https://arxiv.org/pdf/1905.11946.pdf) with experiments with novel ML model based on tiny [mobile transformers](https://arxiv.org/pdf/2110.02178.pdf) to support  underway and will be discussed in a future blog.
8. Most of the project is based on Python and C++ for working with the Azure percept.
9. Docker container provided the on board ML environment for the Azure percept. 
10. Scheduling of routine tasks such as uploading data from devices to the cloud for experimentation was handled by bash scripting (eg using cron)
11. [uhubctl](https://github.com/mvp/uhubctl) came in handy for dealing with usb power status (this was needed to "plug" and "unplug" the camera trap remotely to download data to the rpi

Other notable resources are:
1. Google [coral](https://coral.ai) for off-loading ML acceleration to a usb stick and works with [edge TPU](https://coral.ai/docs/edgetpu/compiler/#help)
2. [Pynq](http://www.pynq.io) board for experimenting with FPGA acceleration (I used this in a class project for [UW CSE 548](https://courses.cs.washington.edu/courses/cse548/) with [Prof. Michael Taylor](http://michaeltaylor.org). This was a lot of fun experimenting with an [open source processor](https://github.com/black-parrot/black-parrot/tree/top_dev) called [Black Parrot](http://michaeltaylor.org/papers/BlackParrot_IEEE_Micro_2020.pdf). A sample setup can be found [here](https://docs.google.com/document/d/1U9XIxLkjbI1vQR5hxjk8SzqqQ3sM2hCMUXfoK3tGwBU/edit#heading=h.x7skb9mp3dd8))
3. Nvidia [Jetson](https://www.nvidia.com/en-us/autonomous-machines/embedded-systems/) another set of embedded AI development boards.
4. [Sabana](https://sabana.io) hardware as code service (kind of like AWS but for testing hardware as code) founded by [Luis Vega](https://homes.cs.washington.edu/~vegaluis/) who guided me through the hardware ecosystem.

As you can readily tell, the spaces is still young but fast growing! Heterogenous devices and development frameworks that one can easily drown in. However, a few mature products are already emerging and (Tensorflow Lite)[https://www.tensorflow.org/lite] is one of them with lots of community backing and quickly supporting more devices. Exchange platforms like ONNX is also instrumental in communicating among the different frameworks.

### The location
Eastern Washington has large stretches of land used entirely for farming. Most of these farms are large multi-million dollar farms belonging to few people. Due to this fact, there are few settlements and this area I worked in is technically considered remote. I was mostly working in Farmington, WA, about a 5 hour drive from Seattle. You can drive for over in that region without proper cellular connection and this is worsened during weather events. During a snow storm, I lost connection for about two hours while driving back to Seattle. Again, the farms do not typically have electric power running through them so the only way to access electricity is through batteries and solar power.
![image2](/files/edge-monitoring_view.jpg)


### Challenges

Weather and access 
The farm is setup on a hilly terrain and so it makes sense to have the observation station on top of the hill. During dry seasons (late spring through early fall), it’s decently easy to go up there with a gator. Though I was hesitant to drive it solo at first, given I was a new driver, it’s actually fun. However, during the winter, it’s much harder to get up there with the gator so you’d go on foot and it’s a good idea to carry handwarmers.
<iframe src="https://drive.google.com/file/d/1JyLXZHJ7rG67fPO_j5dIu89SBoRPyhKX/preview" width="640" height="480" allow="autoplay"></iframe>

When the setup is far from base station but weather is not favorable

When you are working from a far location (with one person to help with the setup)

Working with new hardware with little support (and it getting phased out eventually)

Percept shorted
One of the harder portions of the project was getting the Azure percept ready for use. First, following the tutorial for deploying a custom model (link) successfully took much longer than expected, partly due to esoteric issues that didn't have a lot of community support (leading to a need to swap model layer definitions to those with system support (link some of the errors). I eventually got the system running with a custom model and capturing the camera output and model prediction to the raspberry pi - the central device. Additionally, the percept came with an unconventional power specification that took myself and the farmer (who used to work at Microsoft) some time to figure out a convertor board that provided variable voltage given a fixed 24V suply (from the solar panel). Unfortunately, during one of my hardware debugging sessions, a wire accidentally touched the converter board and shorted it. Afterwards, we were never able to power on the percept :(.

Being at the forefront of the a heterogeneous hardware/software ecosystem with fast moving development

When you have access to TVWS and when you don't 

### Some Lessons

1. Joining Gloire’s paper session made me realize I had been very narrowly focused on what ad hoc solution I can come up with in the moment and that’s there’s actually a wealth of information around research field work that I skipped over. The plan is to delve into the literature for ideas. Who knows? I might have a follow up blog if I find interesting insights.
2. Setting up a remote station to debug from sounds nice in theory but can be challenging in practice. Device fails and you try to get an assistant at the remote site to help you debug over the phone but you get lucky less than half the time in resolving the issue [most likely a good idea to have a replica of the setup with you]
3. Project involved being able to work with hardware (wiring from solar panel and taking a fixed voltage into the voltage and amperage rating of your devices, networking skills to debug when the TVWS router is not detecting your device [other way round?] and of course coding skills to setup remote access) → provide links?
4. In hindsight, the project started with far too many moving parts. Starting with too many moving parts
5. Tension between developing remotely and developing on the ground
6. What reading material did I look for to be better prepared next time?
    
7. Working in isolation

### Multimodal detection
To situate the work in the ML literature, I am working with some existing datasets on low resource multimodal models for species classification. The motivation here is that audio visual edge devices are common and using both modalities is known to improve downstream tasks such as detecting or classifying fine grained species. This will not only beneficial for use cases as this edge detection project but can also make such algorithms more accessible to ecologists who might not have a lot of compute resources for their work. More on this part of the work will be discussed in a future blog post. *TODO: mention collab with Beth and UW fund*

### Conclusion




