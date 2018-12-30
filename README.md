# Tested machines

Lenovo Notebook Yoga 500 - 15ISK with 1x i5-6200U CPU Linux running with Ubuntu Subsystem ( 4.4.0-17134-Microsoft #471-Microsoft Fri Dec 07 20:04:00 PST 2018 x86_64 x86_64 x86_64 GNU/Linux ); Host OS Windows 10 HOME, Build 1803.   
Workstation 1 x AMD with 1 x NVIDIA GTX 1050Ti  running under CentOS 7.4   
Lenovo Ideapad 1 x AMD running under CENTOS7.4   


For this example we assume you have installed python and tensorflow correctly on the plaform  
Python 2.7.12   
Tensorflow 1.12.0   


# CPUvsGPU-Performance-Test
Compare Intel CPU with NVIDIA GTX 1050Ti with CIFAR10 using Tensorflow
In this example I use the famous CIFAR10 benchmark described in here https://en.wikipedia.org/wiki/CIFAR-10
The CIFAR-10 dataset contains 60,000 32x32 color images in 10 different classes, airplanes, cars, birds, cats, deer, dogs, frogs, horses, ships, and trucks.
```
git clone https://github.com/tensorflow/models.git
cd model/tutorials/image/cifar10
python cifar10_train.py
```

Running the CIFAR10 Benchmark
1x Intel(R) Core(TM) i5-6200U CPU @ 2.30GHz, 8GB DDR4 
 yields abut 170 examples/sec.

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


Running the same test on the GPU  

