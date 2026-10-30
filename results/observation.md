Experimental Observations
Experiment 3: Analyze Synchronization Mechanisms in Parallel Programs
1. Individual Program Outputs
Program	Actual Output	Status
Race Condition	Counter = 4969458	Executed
Critical Section	Counter = 10000000	Successful
Atomic Operation	Counter = 10000000	Successful
Barrier	Threads 0 and 1 displayed before and after barrier messages	Successful
Semaphore	Counter = 200000	Successful
2. Comparison Program Results

Number of shared increments: 10,000,000.

Mechanism	Threads	Final Count	Correctness	Time (seconds)
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
3. Additional Thread Testing
Test Command	Output
OMP_NUM_THREADS=4 ./atomic	10000000
OMP_NUM_THREADS=2 ./atomic	10000000
OMP_NUM_THREADS=8 ./atomic	10000000
OMP_NUM_THREADS=4 ./critical	10000000
OMP_NUM_THREADS=4 ./race	2642767
4. Observations
The race condition program produced incorrect counter values due to concurrent unsynchronized updates.
The critical section program maintained the correct counter value for all tested thread counts.
The atomic operation program produced correct results and showed better execution time than critical sections and locks.
The barrier program successfully synchronized the execution of two threads.
The semaphore program correctly produced a final counter value of 200000.
The comparison demonstrated the performance overhead introduced by synchronization mechanisms.
5. Conclusion

The experiment successfully demonstrated different synchronization mechanisms used in parallel programming. Atomic operations provided the best performance among the correct counter-update mechanisms in the observed benchmark. Critical sections, locks, and semaphores ensured safe access to shared resources, while barriers synchronized parallel execution phases.
