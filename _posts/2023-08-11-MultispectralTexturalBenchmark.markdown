---
layout: post
title:  "Multispectral Textural Benchmark - unique cloud application"
date:   2023-08-11 22:25:45 +0100
categories: jekyll update
cover: /images/MultispectralTexturalBenchmark/cover.png
---
<style>
 .center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>

**With the help and supervision of Prof. Michal Haindl I have implemented an unique web application for textural features information quality benchmarking. The application is based in cloud and is currently still in development. I would like to shortly describe the application. I have published a scientific article about the benchmark at 27th KES conference and it will be available in conference journal soon.**  

**Post content**
First the idea is introduced, then the features and future features are explained and in the end the used architecture and technologies brief description is elaborated.  

# Why is there need for such apllication

Texture features are specific data extracted for a wide variety of tasks, such as in computer vision. There are many algorithms for extracting these features, but each one has different characteristics. Although comparative studies have been written, they are often limited by the number of features and the specific testing environment. So there is no tool or resource in which to universally compare textural features. Maybe until now. The developed benchmark does just that. The benchmark can test and evaluate features universally for multispectral data (for any number of spectra).

# Application

I would like to briefly introduce the application. Where you can:
**Managing own experiments**
<img src="/images/MultispectralTexturalBenchmark/my-experiments.png" width="*90*%" class="center">

**Exploring experiments of others**
<img src="/images/MultispectralTexturalBenchmark/public-experiments.png" width="90%" class="center">

**Setup and run an experiment and the view the results in detail**
<img src="/images/MultispectralTexturalBenchmark/experiment.png" width="90%" class="center">

**Visualize the features**
<img src="/images/MultispectralTexturalBenchmark/experiment-visualization.png" width="90%" class="center">

**Future application features**
The benchmark is still in development and I work on it in my free time, there are going to be added following essential application features soon:
- Algorithm comparison
- User input of features

and other application features:
- more features
- more evaluation criteria
- choice of criteria

# Architecture and technologies

It is a web application with cloud computing and symptom evaluation. The entire benchmark is divided into a client application and a server part.

<img src="/images/MultispectralTexturalBenchmark/MUTE-system-architecture.drawio.png" width="89%">

The client application is programmed using the Flutter framework, and since it is a multi-platform technology, it can be deployed not only as a web application but also as a native application for Windows or Linux.

The server part of the application is then created using three servers: a communication server, a solution server and a database server. The communication server serves the web application and provides security and sends requests that it cannot handle to the resolving server (typically requests for the extraction and evaluation of texture features). The solving server then contains a queue for the extraction and evaluation of features, which is served by workers, the amount of which can be scaled and the overall performance of the benchmark can be scaled. Both previously mentioned servers then communicate with the database server (MongoDB), in which they store and retrieve data. In the server part, Python and the Flask framework are used for the most part, but also, for example, binary files compiled from C++ subprograms containing feature extraction algorithms. These are then supplemented with Python subprograms with the same purpose.