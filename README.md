<div align="center">

PGC Experiment 3
Synchronization Mechanisms in Parallel Programs

An experimental study of synchronization techniques in shared-memory parallel programming using C, OpenMP and POSIX Threads.

Programming Language: C
Environment: Ubuntu 24.04 LTS
Compiler: GCC 13.3.0

</div>

1. Overview

This project explores the role of synchronization in shared-memory parallel programming. It implements different synchronization mechanisms and examines their impact on program correctness, execution time and scalability.

The experiment demonstrates how multiple threads interact with shared resources and how synchronization techniques prevent race conditions and maintain data consistency.

The implementation includes individual programs for each synchronization mechanism and a comparative benchmark that evaluates performance across different thread configurations.

2. Concepts Implemented
No.	Synchronization Mechanism	Implementation
01	Race Condition	Unsynchronized shared counter
02	Critical Section	OpenMP critical
03	Atomic Operation	OpenMP atomic
04	Barrier Synchronization	OpenMP barrier
05	Semaphore	POSIX Semaphore
06	Lock	OpenMP Lock
3. Technologies Used
Technology	Application
C	Program implementation
OpenMP	Parallel execution and synchronization
POSIX Threads	Thread management
POSIX Semaphores	Mutual exclusion
GCC	Compilation
Ubuntu	Execution environment
VMware Workstation	Virtualization
4. Repository Structure
text
PGC_Exp-3_Synchronization_Mechanisms/
|
|-- README.md
|
|-- src/
|   |-- race.c
|   |-- critical.c
|   |-- atomic.c
|   |-- barrier.c
|   |-- semaphore.c
|   |-- compare_sync.c
|
|-- screenshots/
|
|-- results/
    |-- observation.md

5. Execution Instructions
Environment Setup

Install the required compiler and development tools.

bash
sudo apt update
sudo apt install build-essential -y


Verify GCC and OpenMP support.

bash
gcc --version

bash
echo '#include <omp.h>' | gcc -E -fopenmp -xc - > /dev/null && echo "OpenMP OK"

Compile and Run Individual Programs

Navigate to the source directory.

bash
cd src


Race Condition

bash
gcc race.c -fopenmp -o race
./race


Critical Section

bash
gcc critical.c -fopenmp -o critical
./critical


Atomic Operation

bash
gcc atomic.c -fopenmp -o atomic
./atomic


Barrier Synchronization

bash
gcc barrier.c -fopenmp -o barrier
./barrier


Semaphore

bash
gcc semaphore.c -pthread -o semaphore
./semaphore


Performance Comparison

bash
gcc compare_sync.c -fopenmp -o compare_sync
./compare_sync

6. Performance Evaluation

The comparison program performs
