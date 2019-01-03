# Tested machines

- Lenovo Ideapad 1 x AMD A6-7310 APU with AMD Radeon R4 Graphics and 16GB RAM running under CENTOS7.4   
- Lenovo Notebook Yoga 500 - 15ISK with 1x i5-6200U CPU Linux running with Ubuntu Subsystem ( 4.4.0-17134-Microsoft #471-Microsoft Fri Dec 07 20:04:00 PST 2018 x86_64 x86_64 x86_64 GNU/Linux ); Host OS Windows 10 HOME, Build 1803.   
- Workstation 1 x AMD FX-6300 6c with 1 x NVIDIA GTX 1050Ti  running under CentOS 7.4, 16GB RAM     



For this example we assume you have installed python and tensorflow correctly on the plaform. For this benchmark I used these versions     
- Python 2.7.12   
- Keras 2.2.4  
- Tensorflow 1.12.0 (Intel)  and 1.10.0 (for AMD)  


# CPUvsGPU-Performance-Test
Compare Intel CPU with NVIDIA GTX 1050Ti with CIFAR10 using Tensorflow
In this example I use the famous CIFAR10 benchmark described in here https://en.wikipedia.org/wiki/CIFAR-10
The CIFAR-10 dataset contains 60,000 32x32 color images in 10 different classes, airplanes, cars, birds, cats, deer, dogs, frogs, horses, ships, and trucks.
```
git clone https://github.com/tensorflow/models.git
cd models/tutorials/image/cifar10
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

- install Java JDK  
```
sudo yum install -y java-11-openjdk-devel.x86_64
```
- set JAVA_HOME
https://tecadmin.net/install-java-8-on-centos-rhel-and-fedora/
- install bazel
Install bazel, followed from: https://gist.github.com/gentaiscool/a628fab5cd98953af7f46b69463394b3
or follow   
https://github.com/bazelbuild/bazel/blob/master/site/docs/install-redhat.md   
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

- Download Tensorflow 
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
Running the same test on the GPU 
