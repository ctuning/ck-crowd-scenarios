CK-powered experiment crowdsourcing scenarios
=============================================

This repository contains public scenarios (software and data sets) in the [Collective Knowledge Format](http://cKnowledge.org)
to crowdsource experiments such as DNN/Caffe crowd-benchmarking and crowd-tuning across diverse mobile devices
provided by volunteers using this [universal Android app](https://github.com/dividiti/crowdsource-video-experiments-on-android).

The results (performance, mispredictions, etc) are continuously 
aggregated in the [open CK repository of knowledge](http://cKnowledge.org/repo).

Normally, you use this repository only for development. Whenever ready, this repository
is updated at cKnowledge.org/repo and scenarios are available 
in [this Android app](https://play.google.com/store/apps/details?id=openscience.crowdsource.video.experiments) 
to let the community participate in collaborative deep learning optimization.

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
* [GitHub Sources](https://github.com/dividiti/crowdsource-video-experiments-on-android)

Android application let volunteers participate in collaborative benchmarking and optimization
of deep learning algorithms. It also sends benchmarking and optimization statistics 
as a JSON blob to the module 'experiment.bench.caffe.mobile' (function "process") 
from the [ck-caffe repository](https://github.com/dividiti/ck-caffe) 
to be aggregated in the [live CK repository](http://cKnowledge.org/repo).

Updating existing scenarios
===========================

If you would like to update existing scenarios
(generate new libcaffe.so and classification binary for Android via CK),
you should copy them to new entries with a version extension.

For example, you can copy entry "bvlc-caffenet-android-recognize-image-v2"
to "bvlc-caffenet-android-recognize-image-v3" via
```
 $ ck cp experiment.scenario.mobile:bvlc-caffenet-android-recognize-image-v2 ck-crowd-scenarios::bvlc-caffenet-android-recognize-image-v3
```

Then you should add key "outdated":"yes" to the meta.json of
"bvlc-caffenet-android-recognize-image-v2" entry. In such case
this entry will be in an "achive" state, will not be updated
and will not be visible for Android app.

You should then update "program" key in a meta.json of the new entry 
with the new version, say 3.0.0.
You also need to substitute v2 with v3 in all keys in meta.json.

After that you should build Caffe libs for all scenarios that will be updated.

For example, for CPU version of Caffe you should run:
```
$ ck install package:lib-caffe-bvlc-master-cpu-universal --target_os=android21-arm64
$ ck install package:lib-caffe-bvlc-master-cpu-universal --target_os=android21-arm-v7a
```
For Caffe OpenCL you should do the following:
```
ck install package:lib-caffe-bvlc-opencl-clblast-universal --target_os=android21-arm64 --env.DISABLE_DEVICE_HOST_UNIFIED_MEMORY=ON
ck install package:lib-caffe-bvlc-opencl-clblast-universal --target_os=android21-arm-v7a --env.DISABLE_DEVICE_HOST_UNIFIED_MEMORY=ON
```

See additional info about building Caffe with various libraries for Android via CK
[here](https://github.com/dividiti/ck-caffe/wiki/Installation).


Note that we suggest you to have a clean installation of all libs. You can do it
by deleting CK env for all software via
```
$ ck rm -f env:*
```
and then removing files from '$USER/CK_TOOLS' directory.

Now you are ready to update new scenarios. You can do it simply as following:
```
$ ck generate experiment.bench.caffe.mobile
```

Normally, all outdated libcaffe.so will be automatically deleted and updated ones will be copied
to the new entries. You can also update only scenarios for a specific engine via
```
$ ck generate experiment.bench.caffe.mobile --prune_engine="Caffe CPU"
 and/or
$ ck generate experiment.bench.caffe.mobile --prune_engine="Caffe OpenCL"
```

Finally, you should automatically update length of files, their MD5
and URLs via 

```
 $ ck process experiment.scenario.mobile
```

Now, new scenarios should be ready to be used by [this Android app](https://play.google.com/store/apps/details?id=openscience.crowdsource.video.experiments) 
if updated at the [cKnowledge.org/repo server](http://cKnowledge.org/repo) - contact authors for more details.

Publications
============

```
@inproceedings{cm:29db2248aba45e59:cd11e3a188574d80,
    title = {{Collective Mind, Part II}: Towards Performance- and Cost-Aware Software Engineering as a Natural Science},
    author = {Fursin, Grigori and Memon, Abdul and Guillon, Christophe and Lokhmotov, Anton},
    booktitle = {18th International Workshop on Compilers for Parallel Computing (CPC'15)},
    year = {2015},
    url = {https://arxiv.org/abs/1506.06256},
    month = {January}
}
```

```
@inproceedings{ck-date16,
    title = {{Collective Knowledge}: towards {R\&D} sustainability},
    author = {Fursin, Grigori and Lokhmotov, Anton and Plowman, Ed},
    booktitle = {Proceedings of the Conference on Design, Automation and Test in Europe (DATE'16)},
    year = {2016},
    month = {March},
    url = {https://www.researchgate.net/publication/304010295_Collective_Knowledge_Towards_RD_Sustainability}
}
```

Public results
==============

Public benchmarking and optimization results are continuously
aggregated in the [live CK repository](http://cKnowledge.org/repo)

Public discussions
==================
* [CK mailing list](http://groups.google.com/group/collective-knowledge)
