# Purpose of this lab

Evaluate the deep learning capabilities of desktop computers using NVIDIA Geforce GPU Engine. 


# Tested machines

- CPU-only: Lenovo Ideapad 1 x AMD A6-7310 APU with AMD Radeon R4 Graphics and 16GB RAM running under CENTOS7.4   
- CPU-only: Lenovo Notebook Yoga 500 - 15ISK with 1x i5-6200U CPU Linux running with Ubuntu Subsystem ( 4.4.0-17134-Microsoft #471-Microsoft Fri Dec 07 20:04:00 PST 2018 x86_64 x86_64 x86_64 GNU/Linux ); Host OS Windows 10 HOME, Build 1803.   
- CPU-only: Microsoft Surface 2 Notebook with 1x i7-8650 CPU CPU Linux running with Ubuntu Subsystem
- GPU equipped Workstation 1 x AMD FX-6300 6c with 1 x NVIDIA GTX 1050Ti running under CentOS 7.4, 16GB RAM, CUDA 9.1 and NVIDIA Driver 390.87. The GPU has 768 cores running with 1.3 GHz and comes with 4 GB GDDR5. The underlying architecture is Pascal.    

For this lab you have installed python and tensorflow correctly on the platform. For this benchmark I used these versions     
- Python 2.7.12   
- Keras 2.2.4  
- Tensorflow 1.12.0 (Intel)  and 1.10.0 (for AMD)  

If you are missing these basics, I recommend to read this very useful guide for beginners    
https://machinelearningmastery.com/setup-python-environment-machine-learning-deep-learning-anaconda/

# CPU vs GPU-Performance-Test

In this lab the famous CIFAR10 benchmark will be used for the evaluation. The Benchmark is described in here https://en.wikipedia.org/wiki/CIFAR-10

The CIFAR-10 dataset contains 60,000 32x32 color images in 10 different classes, airplanes, cars, birds, cats, deer, dogs, frogs, horses, ships, and trucks.
```
git clone https://github.com/tensorflow/models.git
cd models/tutorials/image/cifar10
pip install tensorflow_datasets==1.0.1
python cifar10_train.py
```

Running the CIFAR10 Benchmark
1x Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz, 8GB DDR4 
 yields about 170 examples/sec.

```
2018-12-30 08:25:20.819954: step 2780, loss = 1.22 (177.4 examples/sec; 0.722 sec/batch)
2018-12-30 08:25:27.754323: step 2790, loss = 1.31 (184.6 examples/sec; 0.693 sec/batch)
2018-12-30 08:25:34.844513: step 2800, loss = 1.52 (180.5 examples/sec; 0.709 sec/batch)
2018-12-30 08:25:41.408697: step 2810, loss = 1.25 (195.0 examples/sec; 0.656 sec/batch)
2018-12-30 08:25:48.353929: step 2820, loss = 1.40 (184.3 examples/sec; 0.695 sec/batch)
2018-12-30 08:25:55.261394: step 2830, loss = 1.27 (185.3 examples/sec; 0.691 sec/batch)
2018-12-30 08:26:02.208120: step 2840, loss = 1.36 (184.3 examples/sec; 0.695 sec/batch)
2018-12-30 08:26:09.480962: step 2850, loss = 1.31 (176.0 examples/sec; 0.727 sec/batch)
2018-12-30 08:26:16.246388: step 2860, loss = 1.33 (189.2 examples/sec; 0.677 sec/batch)
2018-12-30 08:26:25.616962: step 2870, loss = 1.38 (136.6 examples/sec; 0.937 sec/batch)
2018-12-30 08:26:32.825914: step 2880, loss = 1.24 (177.6 examples/sec; 0.721 sec/batch)
2018-12-30 08:26:39.423279: step 2890, loss = 1.32 (194.0 examples/sec; 0.660 sec/batch)
2018-12-30 08:26:46.061017: step 2900, loss = 1.48 (192.8 examples/sec; 0.664 sec/batch)
2018-12-30 08:26:52.652775: step 2910, loss = 1.21 (194.2 examples/sec; 0.659 sec/batch)
2018-12-30 08:26:59.737567: step 2920, loss = 1.23 (180.7 examples/sec; 0.708 sec/batch)
2018-12-30 08:27:07.590400: step 2930, loss = 1.40 (163.0 examples/sec; 0.785 sec/batch)
``` 

Running the same benchmark on a Microsoft Surface 2 Notebook with i7-8650 (8c) gives rather similar figures

``` 
2019-01-07 16:33:02.824971: step 170, loss = 3.91 (268.9 examples/sec; 0.476 sec/batch)
2019-01-07 16:33:07.803077: step 180, loss = 3.81 (257.1 examples/sec; 0.498 sec/batch)
2019-01-07 16:33:13.483433: step 190, loss = 3.99 (225.3 examples/sec; 0.568 sec/batch)
2019-01-07 16:33:19.573732: step 200, loss = 3.87 (210.2 examples/sec; 0.609 sec/batch)
2019-01-07 16:33:25.637256: step 210, loss = 3.80 (211.1 examples/sec; 0.606 sec/batch)
2019-01-07 16:33:31.303761: step 220, loss = 3.69 (225.9 examples/sec; 0.567 sec/batch)
2019-01-07 16:33:36.890458: step 230, loss = 3.79 (229.1 examples/sec; 0.559 sec/batch)
2019-01-07 16:33:42.437677: step 240, loss = 3.65 (230.7 examples/sec; 0.555 sec/batch)
2019-01-07 16:33:48.293530: step 250, loss = 3.63 (218.6 examples/sec; 0.586 sec/batch)
2019-01-07 16:33:54.291822: step 260, loss = 3.61 (213.4 examples/sec; 0.600 sec/batch)
2019-01-07 16:34:01.036912: step 270, loss = 3.67 (189.8 examples/sec; 0.675 sec/batch)
2019-01-07 16:34:06.864479: step 280, loss = 3.78 (219.6 examples/sec; 0.583 sec/batch)
2019-01-07 16:34:12.654502: step 290, loss = 3.44 (221.1 examples/sec; 0.579 sec/batch)
2019-01-07 16:34:18.429889: step 300, loss = 3.56 (221.6 examples/sec; 0.578 sec/batch)
2019-01-07 16:34:24.001734: step 310, loss = 3.51 (229.7 examples/sec; 0.557 sec/batch)
``` 
The AMD A6-7310 APU based Notebook (6 cores) yields about 2/3 of the Performance.

![After processing](https://github.com/schoenemeyer/CPUvsGPU-Performance-Test/blob/master/cifar10-ideapad110.png)


The AMD FX-6300 based Workstation yields about the same peformance as the i5-6200U notebook
```
2018-12-31 09:15:35.268013: step 140, loss = 4.00 (203.7 examples/sec; 0.628 sec/batch)
2018-12-31 09:15:41.506636: step 150, loss = 4.30 (205.2 examples/sec; 0.624 sec/batch)
2018-12-31 09:15:47.862790: step 160, loss = 3.86 (201.4 examples/sec; 0.636 sec/batch)
2018-12-31 09:15:54.127954: step 170, loss = 4.13 (204.3 examples/sec; 0.627 sec/batch)
2018-12-31 09:16:00.874560: step 180, loss = 3.73 (189.7 examples/sec; 0.675 sec/batch)
2018-12-31 09:16:07.278367: step 190, loss = 3.94 (199.9 examples/sec; 0.640 sec/batch)
2018-12-31 09:16:13.869336: step 200, loss = 3.73 (194.2 examples/sec; 0.659 sec/batch)
2018-12-31 09:16:20.176501: step 210, loss = 3.68 (202.9 examples/sec; 0.631 sec/batch)
2018-12-31 09:16:26.388101: step 220, loss = 3.73 (206.1 examples/sec; 0.621 sec/batch)
2018-12-31 09:16:32.745433: step 230, loss = 3.70 (201.3 examples/sec; 0.636 sec/batch)
2018-12-31 09:16:39.314489: step 240, loss = 3.74 (194.9 examples/sec; 0.657 sec/batch)
2018-12-31 09:16:45.601244: step 250, loss = 3.62 (203.6 examples/sec; 0.629 sec/batch)
2018-12-31 09:16:52.049265: step 260, loss = 3.71 (198.5 examples/sec; 0.645 sec/batch)
2018-12-31 09:16:58.435356: step 270, loss = 3.52 (200.4 examples/sec; 0.639 sec/batch)
2018-12-31 09:17:04.652128: step 280, loss = 3.78 (205.9 examples/sec; 0.622 sec/batch)
2018-12-31 09:17:11.206604: step 290, loss = 3.63 (195.3 examples/sec; 0.655 sec/batch)
2018-12-31 09:17:17.520113: step 300, loss = 3.42 (202.7 examples/sec; 0.631 sec/batch)
2018-12-31 09:17:23.891535: step 310, loss = 3.50 (200.9 examples/sec; 0.637 sec/batch)
2018-12-31 09:17:30.363019: step 320, loss = 3.42 (197.8 examples/sec; 0.647 sec/batch)
2018-12-31 09:17:36.679483: step 330, loss = 3.40 (202.6 examples/sec; 0.632 sec/batch)
2018-12-31 09:17:42.976991: step 340, loss = 3.35 (203.3 examples/sec; 0.630 sec/batch)

```

In order to get better performance you have to build a Tensorflow package for your specific CPU or GPU. This is possible by using bazel. I followed the instructions on https://github.com/tensorflow/tensorflow/issues/22053 and executed on the AMD Workstation the following steps:   

- Install Java JDK  
```
sudo yum install -y java-11-openjdk-devel.x86_64
```
- set basic Environment Variables such as JAVA_HOME as needed by bazel
https://tecadmin.net/install-java-8-on-centos-rhel-and-fedora/
- Install bazel 
followed from: https://gist.github.com/gentaiscool/a628fab5cd98953af7f46b69463394b3
or follow the instructions from    
https://github.com/bazelbuild/bazel/blob/master/site/docs/install-redhat.md   

If you want to build bazel for Ubuntu 14, 16 or 18, please follow   
https://docs.bazel.build/versions/master/install-ubuntu.html

```
cd /etc/yum.repos.d/
sudo wget https://copr.fedorainfracloud.org/coprs/vbatts/bazel/repo/epel-7/vbatts-bazel-epel-7.repo
cd
sudo yum install -y bazel.x86_64
```

First, lets just install TF from python standard lib so we can get all the dependencies.
```
sudo pip install tensorflow-gpu
```

Now uninstall so we can build from source

```
sudo pip uninstall tensorflow-gpu
```

- Download Tensorflow and prepare compiling with bazel. You will get a number of questions during the configure process.
As abest practice you can follow the responses given in this github   
https://github.com/yaroslavvb/tensorflow-community-wheels/issues/73

```
git clone https://github.com/tensorflow/tensorflow.git
cd tensorflow

./configure

```

- Build Tensorflow with bazel

CPU-only

```
bazel build --config=opt //tensorflow/tools/pip_package:build_pip_package
```
with GPU Support

```
bazel build -c opt --config=cuda //tensorflow/tools/pip_package:build_pip_package
```
If the build is successful, you will see a message like this :

```
INFO: From Compiling tensorflow/core/kernels/broadcast_to_op_gpu.cu.cc:
external/com_google_absl/absl/strings/string_view.h(496): warning: expression has no effect

external/com_google_absl/absl/strings/string_view.h(496): warning: expression has no effect

Target //tensorflow/tools/pip_package:build_pip_package up-to-date:
  bazel-bin/tensorflow/tools/pip_package/build_pip_package
INFO: Elapsed time: 9244.901s, Critical Path: 433.07s
INFO: 11036 processes: 11036 local.
INFO: Build completed successfully, 14151 total actions
[thomas@localhost tensorflow]$ 
```
- Build your local whl file with 

```
bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg
```

Depending on your platform, Compilation will take up to one hour. Once the build is done, you will see a newly built whl file in your temporary directory like shown below

```
[thomas@localhost tensorflow]$ ll /tmp/tensorflow-gpu_pkg
total 128640
-rw-rw-r--. 1 thomas thomas 131725719 Jan  3 17:18 tensorflow-1.12.0-cp27-cp27mu-linux_x86_64.whl
[thomas@localhost tensorflow]$

```
 - Now install your tensorflow package

```
pip install /tmp/tensorflow-gpu_pkg/tensorflow-1.12.0-cp27-cp27mu-linux_x86_64.whl

```
Running the same test on the GPU on the AMD Workstation yields a whopping 5000 examples/sec (!) which is over 25x increase compared to the run without using the Geforce 
```
2019-01-03 17:41:57.641355: step 2600, loss = 1.34 (3019.0 examples/sec; 0.042 sec/batch)
2019-01-03 17:41:57.894708: step 2610, loss = 1.52 (5052.2 examples/sec; 0.025 sec/batch)
2019-01-03 17:41:58.149339: step 2620, loss = 1.52 (5026.9 examples/sec; 0.025 sec/batch)
2019-01-03 17:41:58.405210: step 2630, loss = 1.33 (5002.5 examples/sec; 0.026 sec/batch)
2019-01-03 17:41:58.659363: step 2640, loss = 1.41 (5036.3 examples/sec; 0.025 sec/batch)
2019-01-03 17:41:58.909700: step 2650, loss = 1.55 (5113.1 examples/sec; 0.025 sec/batch)
2019-01-03 17:41:59.163408: step 2660, loss = 1.30 (5045.2 examples/sec; 0.025 sec/batch)
2019-01-03 17:41:59.417626: step 2670, loss = 1.42 (5035.0 examples/sec; 0.025 sec/batch)
2019-01-03 17:41:59.690420: step 2680, loss = 1.46 (4692.2 examples/sec; 0.027 sec/batch)
2019-01-03 17:41:59.956035: step 2690, loss = 1.63 (4819.2 examples/sec; 0.027 sec/batch)
2019-01-03 17:42:00.367474: step 2700, loss = 1.27 (3111.0 examples/sec; 0.041 sec/batch)
2019-01-03 17:42:00.627855: step 2710, loss = 1.37 (4915.8 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:00.887469: step 2720, loss = 1.32 (4930.4 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:01.144161: step 2730, loss = 1.38 (4986.6 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:01.400534: step 2740, loss = 1.30 (4992.7 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:01.656574: step 2750, loss = 1.36 (4999.2 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:01.914569: step 2760, loss = 1.16 (4961.4 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:02.170962: step 2770, loss = 1.30 (4992.4 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:02.425906: step 2780, loss = 1.31 (5020.7 examples/sec; 0.025 sec/batch)
2019-01-03 17:42:02.692558: step 2790, loss = 1.27 (4800.3 examples/sec; 0.027 sec/batch)
2019-01-03 17:42:03.128165: step 2800, loss = 1.37 (2938.4 examples/sec; 0.044 sec/batch)
2019-01-03 17:42:03.385072: step 2810, loss = 1.35 (4982.2 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:03.636899: step 2820, loss = 1.35 (5082.9 examples/sec; 0.025 sec/batch)
2019-01-03 17:42:03.891331: step 2830, loss = 1.44 (5030.8 examples/sec; 0.025 sec/batch)
2019-01-03 17:42:04.143003: step 2840, loss = 1.34 (5086.0 examples/sec; 0.025 sec/batch)
2019-01-03 17:42:04.396034: step 2850, loss = 1.17 (5058.8 examples/sec; 0.025 sec/batch)
2019-01-03 17:42:04.661046: step 2860, loss = 1.28 (4830.0 examples/sec; 0.027 sec/batch)
2019-01-03 17:42:04.915042: step 2870, loss = 1.45 (5039.4 examples/sec; 0.025 sec/batch)
2019-01-03 17:42:05.172771: step 2880, loss = 1.28 (4966.3 examples/sec; 0.026 sec/batch)
2019-01-03 17:42:05.428233: step 2890, loss = 1.22 (5010.5 examples/sec; 0.026 sec/batch)
```

You can check with nvidia-smi -l 2 during the run, and you will see a load between 75% and 85% load on the GPU.

![After processing](https://github.com/schoenemeyer/CPUvsGPU-Performance-Test/blob/master/cifar10-gpu-nvidia-smi.png)

This means a job that may take a day on your Workstation can be done in less than one hour, just by adding a pretty cheap Geforce GTX 1050Ti card with 768 cores and 4 GB GDDR5. 

One might ask how the specific tensorflow version can impact the performance for the I7 Intel processor.
I build tensorflow for the i7 notebook and rerun cifa10_train

python cifar10_train.py

```
2019-01-08 09:50:07.281777: step 10, loss = 4.64 (419.1 examples/sec; 0.305 sec/batch)
2019-01-08 09:50:10.198301: step 20, loss = 4.56 (438.9 examples/sec; 0.292 sec/batch)
2019-01-08 09:50:13.117071: step 30, loss = 4.50 (438.5 examples/sec; 0.292 sec/batch)
2019-01-08 09:50:16.047671: step 40, loss = 4.30 (436.8 examples/sec; 0.293 sec/batch)
2019-01-08 09:50:18.922085: step 50, loss = 4.33 (445.3 examples/sec; 0.287 sec/batch)
2019-01-08 09:50:21.854652: step 60, loss = 4.26 (436.5 examples/sec; 0.293 sec/batch)
2019-01-08 09:50:25.045465: step 70, loss = 4.12 (401.2 examples/sec; 0.319 sec/batch)
2019-01-08 09:50:28.121649: step 80, loss = 4.19 (416.1 examples/sec; 0.308 sec/batch)
2019-01-08 09:50:31.043655: step 90, loss = 4.16 (438.1 examples/sec; 0.292 sec/batch)
2019-01-08 09:50:33.941628: step 100, loss = 4.24 (441.7 examples/sec; 0.290 sec/batch)
2019-01-08 09:50:37.011136: step 110, loss = 4.13 (417.0 examples/sec; 0.307 sec/batch)
2019-01-08 09:50:40.007970: step 120, loss = 4.13 (427.1 examples/sec; 0.300 sec/batch)
2019-01-08 09:50:42.887374: step 130, loss = 4.15 (444.5 examples/sec; 0.288 sec/batch)
2019-01-08 09:50:46.135441: step 140, loss = 3.93 (394.1 examples/sec; 0.325 sec/batch)
```

this is a remarkable improvement compared to the default whl (factor 2).
Therefore, if you are missing a GPU, try to build your own optimized tensorflow version!


Now lets get back to Nvidia GPU. If you are lucky to get a system with a V100 Tesla card you can get way more.
For this test the NGC container  nvcr.io/nvidia/tensorflow:19.02-py3 on a DGX-1 system.
```
python cifar10_train.py
```
```
2019-03-19 12:24:39.452905: step 99650, loss = 0.74 (26329.9 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:39.503508: step 99660, loss = 0.89 (25301.8 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:39.552622: step 99670, loss = 0.83 (26055.0 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:39.601304: step 99680, loss = 0.55 (26292.8 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:39.653642: step 99690, loss = 0.84 (24456.8 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:39.842918: step 99700, loss = 0.69 (6763.3 examples/sec; 0.019 sec/batch)
2019-03-19 12:24:39.894984: step 99710, loss = 0.72 (24574.9 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:39.943606: step 99720, loss = 0.68 (26325.6 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:39.993851: step 99730, loss = 0.70 (25475.5 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.044455: step 99740, loss = 0.77 (25294.2 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.096368: step 99750, loss = 0.62 (24657.9 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.144780: step 99760, loss = 0.70 (26439.2 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.193661: step 99770, loss = 0.97 (26185.0 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.242644: step 99780, loss = 0.82 (26132.6 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.297793: step 99790, loss = 0.74 (23208.7 examples/sec; 0.006 sec/batch)
2019-03-19 12:24:40.487197: step 99800, loss = 0.84 (6758.5 examples/sec; 0.019 sec/batch)
2019-03-19 12:24:40.540311: step 99810, loss = 0.66 (24093.4 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.588428: step 99820, loss = 0.77 (26601.7 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.643405: step 99830, loss = 0.52 (23286.9 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.691324: step 99840, loss = 0.78 (26705.9 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.741098: step 99850, loss = 0.64 (25716.4 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.790251: step 99860, loss = 0.77 (26041.0 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.842583: step 99870, loss = 0.65 (24459.9 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.892506: step 99880, loss = 0.61 (25638.9 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:40.940998: step 99890, loss = 0.71 (26396.4 examples/sec; 0.005 sec/batch)
2019-03-19 12:24:41.130107: step 99900, loss = 0.54 (6768.6 examples/sec; 0.019 sec/batch)
```


