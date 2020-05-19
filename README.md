# Introduction

This repository contains code samples for Michael Nielsen's book [Neural Networks and Deep Learning][1].

The code is modified or python 3.x. The original code is written for Python 2.6 or Python 2.7 and you can find the original code at [github][2]. The origin purpose for which I create this repository is to study Neural Network and help others who want to study it and need the source code. I'm quite willing to discuss it with anyone.
##Installing python3.x
You should install [python interpreter][3] on your computer before you clone this repository. The latest version of python now is python3.5.2 which is intalled on my computer. The steps of intalling python are very easy and you can use [Google][4] if you have any question about it.

## Installing NumPy and SciPy

It is a little difficult for python3.x to install [NumPy][5] and [SciPy][7]. 

Numpy is the fundamental package for scientific computing with python. it contains among other things:
* a powerful N-dimensional array object
* sophisticated(broadcasting) funcions
* tools for integrating C/C++ and Fortran code
* useful linear algebra, Fourier transform, and random number capabilities

The NumPy installation package can be found [here][6]. The names of intallation packages are follow the following rules:

	cpxx_OperatingSystem_The architecture of CPU

cpxx means the interpreter of python whose verison is python x.x is written by C. OperatingSystem can be Macoxsx,linux or win. The architecture of CPU can be x86, amd64 or i686.

SciPy is open-source software for mathematics, science, and engineering. The SciPy library depends on NumPy.The SciPy library is built to work with NumPy arrays, and provides many user-friendly and efficient numerical routines for numerical integration and optimization. The rule of name of SciPy is similar to that of Numpy.

So choose the version which is suitable for your computer and the interpreter of python.

Unfortulately, it's diffcult for windows platform to install scipy. The binary executed file .whl is not supported for windows platform because some requirements for compiling scipy source files isn't supported on windows platform.
So, one of some solutions to slove this problem is to install the packages of the SciPy statck. It's easy to search lots of informations on it online. But here I will provide another way
to install scipy package. Christoph Gohlke provides [pre-built Windows installers][18] for many Python packages, including all of the core SciPy stack, which work extremely well.


## Installing matplotlib
matplotlib is very easy to be installed in order to plot some figures using MATLAB syntax. The only thing you need to do is just type the following command in your bash

	pip install matplotlib

## Installing Theano

[Theano][17] is a Python library that allows you to define, optimize, and evaluate mathematical expressions involving multi-dimensional arrays efficiently.Teano features:

* **tight integration with NumPy** - Use numpy.ndarray in Theano-compiled functions.
* **transparent use of a GPU** - Perform data-intensive calculations up to 140x faster with CPU.
* **efficient symbolic differentiation** – Theano does your derivatives for function with one or many inputs.**
* **speed and stability optimizations** – Get the right answer for `log(1+x)` even when `x` is really tiny.
* **dynamic C code generation** – Evaluate expressions faster.
* **extensive unit-testing and self-verification** – Detect and diagnose many types of errors.

Type the following command on Bash to install Theano.

	pip install theano
	
Before installing theano you should install numpy and scipy.

## Modifying code samples for python 3.x
Now we could make some changes for code samples in order to run our code samplesthrough python 3.x interpreter after some fundamental packages has been installed. The differences between files for python 2.x and python 3.0 will be listed below and some descriptions have been added for this changes.

### mnist_loader.py
The functions of [mnist_loader.py][8] file are load the training data, validation data and test data and change their form which is conveniently manipulated by python. The codes we have changed are

> [Line 13][9]:    import pickle

> Unmodified: import cPickle

> [Line 43][10]:    training_data, validation_data, test_data = pickle.load(f,encoding='iso-8859-1')

> Unmodified: training_data, validation_data, test_data = cPickle.load(f)

> [Line 71][11]:    training_data = list(zip(training_inputs, training_results))

> Unmodified: training_data = zip(training_inputs, training_results)

> [Line 73][12]:    validation_data = list(zip(validation_inputs, va_d[1]))

> Unmodified: validation_data = zip(validation_inputs, va_d[1])

> [Line 75][13]:    test_data = list(zip(test_inputs, te_d[1]))

> Unmodified: test_data = zip(test_inputs, te_d[1])

Module cPickle is written by c for python 2.x and it has been cancelled in python 3.x. So we instead use statement "import pickle". The effects of module pickle are depend on the version of python. If we don't pass the encoding argument python 3.x will throw an exception. For Line 71,73,75 the only thing we need to do is just make a convertion. In python 3.x the object returned by zip() isn't a list. It is an object which returns the successive items of the desired sequence when we iterate over it. It doesn't really make the list, thus saving space. we say such an object is iterable, that is, suitable as a target for functions and constructs that expect something from which they can obtain successive items until the supply is exhausted. So such "len(iterable object)" is wrong and we have to convert it into a list using "list(len(iterable object))".

### ./chapter1_2/Network.py
`xrange()` is removed in python 3.x, so in this file we need to replace all `xrange()` into `range()`.
The differences between two versions are

> [Line 35][14]:    for j in range(epochs):

> Unmodified: for j in xrange(epochs):

> [Line 38][15]:    for k in range(0, n, mini_batch_size)]

> Unmodified: for k in xrange(0, n, mini_batch_size)]

> [Line 90][16]:    for l in range(2, self.num_layers):

> Unmodified: for l in xrange(2, self.num_layers):

What's more, the syntax of 'print' in python3.x need to followed by a pair of parent parentheses.

In the end of this file, I type some statements to run this network. So if you want to see the effect of this
network, the only thing you just need to do is type the following command on your Bash.

	python Network.py
	

[1]: http://neuralnetworksanddeeplearning.com/
[2]: https://github.com/mnielsen/neural-networks-and-deep-learning
[3]: https://www.python.org/downloads/
[4]: https://www.google.com
[5]: http://www.numpy.org/
[6]: https://pypi.python.org/pypi/numpy
[7]: https://pypi.python.org/pypi/scipy
[8]: ./mnist_loader.py
[9]: ./mnist_loader.py#L13
[10]: ./mnist_loader.py#L43
[11]: ./mnist_loader.py#L71
[12]: ./mnist_loader.py#L73
[13]: ./mnist_loader.py#L75
[14]: ./chapter1_2/Network.py#L35
[15]: ./chapter1_2/Network.py#L38
[16]: ./chapter1_2/Network.py#L90
[17]: http://www.deeplearning.net/software/theano/
[18]: http://www.lfd.uci.edu/~gohlke/pythonlibs/


