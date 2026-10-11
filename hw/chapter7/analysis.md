# Question 1: Compare FIFO, SJF, RR
Job list: 100, 200, 300

## FIFO
Average Response time: 133.33
Average Turnaround time: 333.33
Average Wait time: 133.33
Execution order: Job0 → Job1 → Job2

## SJF
Average Response time: 133.33
Average Turnaround time: 333.33
Average Wait time: 133.33
Since all jobs arrive at time 0 and are already sorted by running time, SJF produces exactly the same execution sequence and statistics as FIFO.

## RR (time slice q=100)
Average Response time: 100.00
Average Turnaround time: 366.67
Average Wait time: 166.67
Execution trace: Job0 → Job1 → Job2 → Job1 → Job2
RR achieves better average response time, which is suitable for interactive systems. However, its average turnaround and waiting time are worse than FIFO/SJF.

### Summary
FIFO and SJF are good for batch jobs. RR reduces response time for interactivity, but increases overall waiting and turnaround time.# Question 2
For what workloads and quantum lengths does SJF deliver the same response times as Round-robin scheduling?

## Experiment
Job list: 100, 200, 300
RR with quantum q=300.
Average Response time: 133.33, same as SJF.

## Explanation
When the RR time slice (quantum) is **greater than or equal to the maximum job running time**, RR will not preempt any running job. Once a job gets the CPU, it runs until completion.
If all jobs arrive at time 0 and we schedule shorter jobs first, RR behaves exactly like non-preemptive SJF. The response times become identical.

### Conclusion
Workload condition: all jobs arrive at time 0.
Quantum condition: quantum ≥ the longest job’s runtime.# Question 3
What happens to response time with SJF as job lengths increase? Explain.

## Experiment
Case1: jobs [100, 200, 300], SJF average response time = 133.33
Case2: jobs [200, 400, 600], SJF average response time = 266.67

## Explanation
In non-preemptive SJF, a job’s response time is the total runtime of all jobs scheduled before it.
When every job’s length increases proportionally, the waiting time for later jobs grows linearly.
As job lengths get larger, the average response time increases proportionally.

### Conclusion
For SJF, if all job lengths increase, the average response time increases linearly. Longer jobs make subsequent jobs wait longer.