# Simplified SMO for Support Vector Machines (SVM) in C++



A lightweight, from-scratch C++ implementation of the **Simplified Sequential Minimal Optimization (SMO)** algorithm for training binary Support Vector Machines (SVM) without external machine learning dependencies.



---



## Overview



This repository provides a clear, self-contained implementation of the Simplified SMO optimization algorithm. It solves the dual quadratic programming problem associated with Support Vector Machines using a linear dot-product kernel, making it suitable for educational purposes, benchmarking, or lightweight embedded environments.



### Key Features

* **From-Scratch Optimization:** Implements Lagrange multiplier ($\alpha$) pair updates, KKT condition tolerance checks, error caching ($E_i$), and bias ($b$) threshold calculation.

* **Flexible Data Loading:** Supports reading custom training and validation datasets from an external text file (`data.txt`), with an automatic fallback to a built-in template dataset if the file is unavailable.

* **Standard Library Only:** Built exclusively with the C++ Standard Library (`<vector>`, `<fstream>`, `<random>`, `<iostream>`).



---



## Architecture



* **`simpified_SMO` Class:** Encapsulates the SVM model parameters ($C$, $\text{tol}$, $\text{max\_passes}$), training loop (`train()`), inference method (`predict()`), and linear dot-product kernel (`dotProduct()`).

* **`readFromFile()`:** Parses structured input data containing support vector coordinates, binary class labels (`-1` or `1`), and validation samples.

* **`main()`:** Initializes the dataset, configures the model hyperparameters, executes training, outputs the learned bias and $\alpha$ values, and runs predictions on the validation set.



---



## Input File Specification (`data.txt`)



To use custom training and testing data, create a `data.txt` file in the expected relative path (`../../data.txt` by default) adhering to the following schema:



```text

5              // Number of training vectors (n)

x1 y1          // 2D feature coordinates for each training vector

x2 y2

x3 y3

x4 y4

x5 y5

label1         // Corresponding binary class labels (-1 or 1)

label2

label3

label4

label5

2              // Number of validation vectors to classify

x1 y1          // 2D feature coordinates for each validation vector

x2 y2

```



---



## Build and Execution



### Prerequisites

* A C++ compiler supporting the C++11 standard or newer (e.g., `g++`, `clang++`, or MSVC).



### Compilation

Compile the source code using `g++`:



```bash

g++ -std=c++11 -O2 main.cpp -o svm_smo

```



### Execution

Run the compiled binary:



```bash

./svm_smo

```



---



## References



The mathematical formulation and algorithmic structure of this implementation are based on the following resources:



1. **Stanford CS229 Lecture Notes:** [The Simplified SMO Algorithm](https://cs229.stanford.edu/materials/smo.pdf)

2. **Bitmask93 Technical Blog:** [Sequential Minimal Optimization for Support Vector Machines](https://bitmask93.github.io/ml-blog/Sequential-Minimal-Optimization-for-Support-Vector-Machines/)

3. **Wikipedia:** [Sequential Minimal Optimization](https://en.wikipedia.org/wiki/Sequential_minimal_optimization)
