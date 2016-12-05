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

* Grigori Fursin, dividiti (UK)
* Anton Lokhmotov, dividiti (UK)

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

Update
======

When new scenario is available, you should run the following command
from ck-crowdtuning repository to process all meta
and automatically calculate MD5, file sizes, etc:

```
 $ ck process experiment.scenario.mobile
```

Android application
===================

* [GooglePlay](https://play.google.com/store/apps/details?id=openscience.crowdsource.video.experiments)
* [GitHub](https://github.com/dividiti/crowdsource-video-experiments-on-android)

Android application send benchmarking and optimization statistic as a JSON blob
to the module 'experiment.bench.caffe.mobile' (function process) 
from the [ck-caffe](https://github.com/dividiti/ck-caffe) repo.

Public results
==============

Public benchmarking and optimization results are continuously
aggregated in [CK live repo](http://cKnowledge.org/repo)
