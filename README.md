CK-powered experiment crowdsourcing scenarios
=============================================

Public scenarios to crowdsource experiments (such as Caffe 
crowd-benchmarking and crowd-tuning) using mobile devices.

Status
======
On-going (stable version is available).

Prerequisites
=============
* Collective Knowledge framework ([@GitHub](http://github.com/ctuning/ck))
* python (with imaging and matplotlib)
* git client
* Android NDK

Authors
=======

* Grigori Fursin, dividiti
* Anton Lokhmotov, dividiti
* Daniil Efremov, Xored

License
=======
* BSD, 3-clause

Installation
============

```
$ sudo apt-get install python python-pip git
$ sudo pip install ck
```

```
 $ ck pull repo:ck-crowd-scenarios
```

Android application
===================

* [GooglePlay](https://play.google.com/store/apps/details?id=openscience.crowdsource.video.experiments)
* [GitHub](https://github.com/dividiti/crowdsource-video-experiments-on-android)

Android application send benchmarking and optimization statistic as a JSON blob
to the module 'experiment.bench.caffe.mobile' (function process) 
from the [ck-caffe](https://github.com/dividiti/ck-caffe) repo.

Generating libcaffe.so and classification via CK
================================================
It is possible to automatically generate libcaffe.so and classification
for ARM64 and ARM32 via CK with all meta via:
```
$ ck generate experiment.bench.caffe.mobile
```

This module is available in 'ck-caffe' repository.

Note, that if outdated lib and bin are found, they will be removed.
Therefore, please copy old files manually to the 'ck-crowd-scenarios-arc' repo
before using this command!

When new scenario is available, you should run the following command
from ck-crowdtuning repository on server sie to process all meta
and automatically calculate MD5, file sizes, URL, etc:

```
 $ ck process experiment.scenario.mobile
```

Public results
==============

Public benchmarking and optimization results are continuously
aggregated in [CK live repo](http://cKnowledge.org/repo)
