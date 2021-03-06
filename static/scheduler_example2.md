---
layout: doc
title: "Example2"
permalink: scheduler_example2
---

Example 2
=========

Consider the following simple schedule:

| job number | arrival time | running time | priority |
|------------|--------------|--------------|----------|
| 0          | 0            | 8            | 1        |
| 1          | 1            | 8            | 1        |
| 2          | 3            | 4            | 2        |

The flow of execution of functions calls is as follows:

```
 scheduler_start_up(s = SJF)
     --> scheduler initialized

 scheduler_new_job(job_number = 0, time = 0, running_time = 8, priority = 1)
     --> returns true, indicating that job(id=0) should be scheduled at this time.

 scheduler_new_job(job_number = 1, time = 1, running_time = 8, priority = 1)
     --> returns false, indicating that job(id=1) will not be scheduled at this time.

 scheduler_new_job(job_number = 2, time = 3, running_time = 4, priority = 2)
     --> returns false, indicating that job(id=2) will not be scheduled at this time.

 scheduler_job_finished(job_number = 0, time = 8)
     --> returns 2, indicating that job(id=2) should be run next on the processor.

 scheduler_job_finished(job_number = 2, time = 12)
     --> returns 1, indicating that job(id=1) should be run next on the processor.

 scheduler_job_finished(job_number = 1, time = 20)
     --> returns -1, indicating that the processor should remain idle.

 scheduler average waiting time()
     --> returns (16/3) == 5.33

 scheduler average turnaround time()
     --> returns (36/3) == 12.00

 scheduler average response time()
     --> returns (16/3) == 5.33

 scheduler_clean_up()
     --> cleans up and frees all memory used by the scheduler
```
When the simulator is executed and the flow of execution is implemented correctly, you will see the following output:

```
Loaded 3 job(s) using Non-preemptive Shortest Job First (SJF) scheduling...

=== [TIME 0] ===
A new job, job 0 (running time=8, priority=1), arrived. Job 0 is now running on processor.
  Queue: 

At the end of time unit 0...
  History: 0

  Queue: 

=== [TIME 1] ===
A new job, job 1 (running time=8, priority=1), arrived. Job 1 is set to idle (-1).
  Queue: 

At the end of time unit 1...
  History: 00

  Queue: 

=== [TIME 2] ===
At the end of time unit 2...
  History: 000

  Queue: 

=== [TIME 3] ===
A new job, job 2 (running time=4, priority=2), arrived. Job 2 is set to idle (-1).
  Queue: 

At the end of time unit 3...
  History: 0000

  Queue: 

=== [TIME 4] ===
At the end of time unit 4...
  History: 00000

  Queue: 

=== [TIME 5] ===
At the end of time unit 5...
  History: 000000

  Queue: 

=== [TIME 6] ===
At the end of time unit 6...
  History: 0000000

  Queue: 

=== [TIME 7] ===
At the end of time unit 7...
  History: 00000000

  Queue: 

=== [TIME 8] ===
Job 0 finished. Processor is now running job 2.
  Queue: 

At the end of time unit 8...
  History: 000000002

  Queue: 

=== [TIME 9] ===
At the end of time unit 9...
  History: 0000000022

  Queue: 

=== [TIME 10] ===
At the end of time unit 10...
  History: 00000000222

  Queue: 

=== [TIME 11] ===
At the end of time unit 11...
  History: 000000002222

  Queue: 

=== [TIME 12] ===
Job 2 finished. Processor is now running job 1.
  Queue: 

At the end of time unit 12...
  History: 0000000022221

  Queue: 

=== [TIME 13] ===
At the end of time unit 13...
  History: 00000000222211

  Queue: 

=== [TIME 14] ===
At the end of time unit 14...
  History: 000000002222111

  Queue: 

=== [TIME 15] ===
At the end of time unit 15...
  History: 0000000022221111

  Queue: 

=== [TIME 16] ===
At the end of time unit 16...
  History: 00000000222211111

  Queue: 

=== [TIME 17] ===
At the end of time unit 17...
  History: 000000002222111111

  Queue: 

=== [TIME 18] ===
At the end of time unit 18...
  History: 0000000022221111111

  Queue: 

=== [TIME 19] ===
At the end of time unit 19...
  History: 00000000222211111111

  Queue: 

=== [TIME 20] ===
Job 1 finished. Processor is now running job -1.
  Queue: 

FINAL TIMING DIAGRAM:
  History: 00000000222211111111

Average Waiting Time: 5.33
Average Turnaround Time: 12.00
Average Response Time: 5.33
```
