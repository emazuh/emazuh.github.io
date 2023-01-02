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

With advances in remote sensing technology, there is excitment around new ways to tackle some of the sustainable developing goals. In this project, I focus on goals 2 (addressing food security) and 15 (protect and restore terrestrial ecosystems) while being mindful of goal 13 (combating climate change). Even though my end goal is for use cases in developing countries, I had a test bed in a farm in Eastern Washington that had limited access to cellular networks and limited access to power supply. *TODO: add summary*

## The Setup

### Devices
For this project, I started with three edge devices - an android phone, a raspberry pi and a Microsoft Azure Percept (link). I also had a standard camera trap in the setup to use as a comparison point with a standard device in the environmental monitoring community. Frameworks I use in this project include Pytorch, Android Studio, Python for most of the code implementation and C++ for dealing with Azure percept. I used Azure blob storage and Azure ML Studio (double check). I started with YoloV3 (tiny - {param count}). ONNX for model conversion in the tiny devices ecosystem. Bash scripting was used for running scheduled jobs such as data upload.
![image1](/files/edge-devices.jpg)


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




