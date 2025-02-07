# Parallel-Search-Multi-Threading-Multi-Processing

## **Overview**
This project implements a **parallel search algorithm** using both **multi-threading and multi-processing** techniques. The goal is to search for a target value in a large integer array while comparing the efficiency of **threads vs. processes**.

## **Files**
- **`multitest_proc.c`** – Implements the search using multiple processes.
- **`multitest_thread.c`** – Implements the search using multiple threads.
- **`multitest.h`** – Provides a macro for `find()`, mapping it to the correct search function.
- **`searchtest.c`** – Runs multiple test cases and collects performance metrics.
- **`results.pdf`** – Documents the experimental results.
- **`testplan.pdf`** – Describes the testing methodology and expected outcomes.

## **Key Features**
- **Parallelized Search**  
  - Uses **processes (`fork`)** or **threads (`pthread_create`)** to split search workload.  
  - Divides an array into blocks and assigns each block to a separate process/thread.  
  - Returns the index of the target value if found; otherwise, returns `-1`.

- **Performance Analysis**  
  - Runs multiple test cases with different array sizes and block sizes.  
  - Compares execution time for **multi-processing vs. multi-threading**.  
  - Calculates **average execution time, standard deviation, and process/thread switch times**.

- **Dynamic Block Allocation**  
  - Allows varying block sizes (default **250** elements per block).  
  - Prevents exceeding `ulimit` when spawning processes.

## **Test Cases**
The program includes six test cases that evaluate efficiency under different scenarios:
- **Test 1:** Search for a missing element in an array of **1000** elements.
- **Test 2:** Search for an element in an array of **54321** elements.
- **Test 3:** Search for the **first element** in a shuffled array.
- **Test 4:** Search for an element in a **large array (100,000 elements)**.
- **Test 5 & 6:** Compare block sizes (**100 vs. 250**) to evaluate the impact on performance.

Additional **benchmarking functions**:
- **`allTests()`** – Runs all test cases **100 times** and computes performance metrics.
- **`tradeOff()`** – Evaluates performance across different array sizes.

## **How to Run**
### **Compiling the Program**
To compile for **multi-processing**:
```sh
gcc -o proc_search searchtest.c multitest_proc.c -lpthread
```
To compile for **multi-threading**:
```sh
gcc -o thread_search searchtest.c multitest_thread.c -lpthread
```
