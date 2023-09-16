---
layout: post
title:  "Multispectral Textural Benchmark"
date:   2023-08-11 22:25:45 +0100
categories: jekyll update
cover: /images/MultispectralTexturalBenchmark/cover.png
---

**With the help and supervision of Prof. Michal Haindl I have implemented an unique web application for textural features information quality benchmarking. The application is based in cloud and is currently still in development. I would like to shortly describe the application.**  

Texture features are specific data extracted for a wide variety of tasks, such as in computer vision. There are many algorithms for extracting these features, but each one has different characteristics. Although comparative studies have been written, they are often limited by the number of features and the specific testing environment. So there is no tool or resource in which to universally compare textural features. Maybe until now. The developed benchmark does just that. The benchmark can test and evaluate features universally for multispectral data (for any number of spectra).

<img style="float:right;" src="/images/MultispectralTexturalBenchmark/mute_exp.png" width="49%">

It is a web application with cloud computing and symptom evaluation. The entire benchmark is divided into a client application and a server part.

<img src="/images/MultispectralTexturalBenchmark/MUTE-system-architecture.drawio.png" width="89%">

The client application is programmed using the Flutter framework, and since it is a multi-platform technology, it can be deployed not only as a web application but also as a native application for Windows or Linux.

The server part of the application is then created using three servers: a communication server, a solution server and a database server. The communication server serves the web application and provides security and sends requests that it cannot handle to the resolving server (typically requests for the extraction and evaluation of texture features). The solving server then contains a queue for the extraction and evaluation of features, which is served by workers, the amount of which can be scaled and the overall performance of the benchmark can be scaled. Both previously mentioned servers then communicate with the database server (MongoDB), in which they store and retrieve data. In the server part, Python and the Flask framework are used for the most part, but also, for example, binary files compiled from C++ subprograms containing feature extraction algorithms. These are then supplemented with Python subprograms with the same purpose.