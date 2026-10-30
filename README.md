PGC_Exp-3_Synchronization_Mechanisms
Experiment 3: Analyze Synchronization Mechanisms in Parallel Programs
1. Objective

To implement and study common synchronization mechanisms used in shared-memory parallel programs, including race conditions, critical sections, atomic operations, barriers, semaphores, and locks.

To evaluate their correctness, execution time, and scalability as the number of threads increases.

2. Software Requirements
Software / Tool	Purpose
VMware Workstation Pro	Virtualization software
Ubuntu 24.04 LTS	Operating system
GCC 13.3.0	C compiler
OpenMP	Parallel programming support
POSIX Threads	Thread management
Semaphore Library	Process synchronization
3. Synchronization Mechanisms
Race Condition: Demonstrates incorrect shared-variable updates without synchronization.
Critical Section: Ensures only one thread accesses the shared variable at a time.
Atomic Operation: Performs indivisible updates on shared variables.
Barrier: Synchronizes threads at a common execution point.
Semaphore: Controls access to shared resources.
Lock: Provides mutual exclusion during shared-variable updates.
4. Project Structure
text
PGC_Exp-3_Synchronization_Mechanisms/
│
├── README.md
├── src/
│   ├── race.c
│   ├── critical.c
│   ├── atomic.c
│   ├── barrier.c
│   ├── semaphore.c
│   └── compare_sync.c
│
├── screenshots/
│
└── results/
    └── observation.md

5. Installation

Update Ubuntu:

bash
sudo apt update


Install GCC:

bash
sudo apt install build-essential -y


Verify GCC:

bash
gcc --version


Verify OpenMP:

bash
echo '#include <omp.h>' | gcc -E -fopenmp -xc - > /dev/null && echo "OpenMP OK"

6. Compilation and Execution

Navigate to the source directory:

bash
cd src


Program 1: Race Condition

bash
gcc race.c -fopenmp -o race
./race


Program 2: Critical Section

bash
gcc critical.c -fopenmp -o critical
./critical


Program 3: Atomic Operation

bash
gcc atomic.c -fopenmp -o atomic
./atomic


Program 4: Barrier

bash
gcc barrier.c -fopenmp -o barrier
./barrier


Program 5: Semaphore

bash
gcc semaphore.c -pthread -o semaphore
./semaphore


Program 6: Comparison and Performance Analysis

bash
gcc compare_sync.c -fopenmp -o compare_sync
./compare_sync

7. Thread Configuration

The OpenMP programs can be executed with different thread counts.

Example:

bash
OMP_NUM_THREADS=2 ./atomic
OMP_NUM_THREADS=4 ./atomic
OMP_NUM_THREADS=8 ./atomic


The comparison program automatically tests 1, 2, 4, and 8 threads.

8. Experimental Results

The comparison program evaluates four synchronization mechanisms using 10,000,000 shared counter increments.

Mechanism	Threads	Final Count	Correctness	Execution Time (s)
None	1	10000000	Correct	0.0061
Critical	1	10000000	Correct	0.0950
Atomic	1	10000000	Correct	0.0519
Lock	1	10000000	Correct	0.0862
None	2	6691331	Incorrect	0.0080
Critical	2	10000000	Correct	0.2273
Atomic	2	10000000	Correct	0.0731
Lock	2	10000000	Correct	0.2890
None	4	6329100	Incorrect	0.0068
Critical	4	10000000	Correct	0.1865
Atomic	4	10000000	Correct	0.0683
Lock	4	10000000	Correct	0.2582
None	8	7653234	Incorrect	0.0071
Critical	8	10000000	Correct	0.2404
Atomic	8	10000000	Correct	0.0823
Lock	8	10000000	Correct	0.2687

Note: Execution times may vary depending on processor configuration and system load. The unsynchronized program has a data race, so its output is unpredictable.

9. Observations
Race conditions produce unpredictable results due to unsynchronized access.
Critical sections ensure correctness but introduce waiting overhead.
Atomic operations provide efficient synchronization for simple shared-variable updates.
Barriers synchronize the execution phases of parallel threads.
Semaphores provide controlled access to shared resources.
Locks ensure mutual exclusion but may reduce scalability due to contention.
10. Conclusion

The experiment demonstrates different synchronization mechanisms used in shared-memory parallel programming.

Atomic operations provide a good balance between correctness and performance for simple shared-variable updates. Critical sections, locks, and semaphores ensure mutual exclusion but introduce synchronization overhead. Barrier synchronization coordinates parallel execution phases.

The experiment highlights the importance of selecting appropriate synchronization mechanisms to maintain correctness and improve parallel program performance.
