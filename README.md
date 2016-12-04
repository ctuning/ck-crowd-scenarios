# ck-crowd-scenarios
Public scenarios to crowdsource experiments (such as Caffe crowd-benchmarking and crowd-tuning using mobile devices)

When new scenario is available, you should run the following command
from ck-crowdtuning repository to process all meta
and automatically calculate MD5, file sizes, etc:

```
 $ ck process experiment.scenario.mobile
```

Associated Android application:

* (GooglePlay)[https://play.google.com/store/apps/details?id=openscience.crowdsource.video.experiments]
* (GitHub)[https://github.com/dividiti/crowdsource-video-experiments-on-android]

Android application send benchmarking and optimization statistic as a JSON blob
to the module 'experiment.bench.caffe.mobile' (function process) 
from the (ck-caffe)[https://github.com/dividiti/ck-caffe] repo.

