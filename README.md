# StackCanariesPerfEffect

## Table of Contents
- [Introduction](#introduction)
- [Build and Run](#build-and-run)
- [Possible Output](#possible-output)
- [Results](#results)

## Introduction
This project benchmarks the performance impact of stack canaries in C++ programs. Benchmarks are done on my other project [MatMulAlgorithms](https://github.com/Hayk10002/MatMulAlgorithms) which implements several algorithms for multiplying two matrices. The performance is measured with and without stack canaries enabled, to see how much they affect the performance of the algorithms.

## Build and Run
To clone and run this project, you'll need [Git](https://git-scm.com) and [CMake](https://cmake.org/) installed on your computer. From your command line:

```bash
# Clone this repository
$ git clone https://github.com/Hayk10002/StackCanariesPerfEffect

# Go into the repository
$ cd StackCanariesPerfEffect

# Generate the build files
$ cmake -DCMAKE_BUILD_TYPE=Release [-DMULTIPLIER={some multiplier}] -S . -B build
# you can see all multipliers by running one of the generated executables in build directory with --help flag

# Build the project
$ cmake --build build --config Release

# Then, run ctest to run the benchmarks
$ ctest --test-dir build
```

## Possible Output
(for the default multiplier - hybrid)
```
Internal ctest changing into directory: /path/to/build
Test project /path/to/build
    Start 1: WithCanariesTest
1/2 Test #1: WithCanariesTest .................   Passed    2.41 sec
    Start 2: WithoutCanariesTest
2/2 Test #2: WithoutCanariesTest ..............   Passed    2.52 sec

100% tests passed, 0 tests failed out of 2

Total Test time (real) =   4.95 sec
```

## Results

The results of the benchmarks show that the performance impact of stack canaries is non observable, in fact I've tried different multipliers and the results are very similar. The performance difference is within the margin of error, which means that stack canaries do not have a significant impact on the performance of the algorithms implemented in the MatMulAlgorithms project.