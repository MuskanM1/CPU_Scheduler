# CPU Scheduler using MultiThreading

## Table of contents
* [General info](#general-info)
* [Technologies](#technologies)
* [Usage](#usage)
* [Summary](#Summary)
* [Results](#Results)
* [Report Link](#report-Link)


## General info
This project is Java implementation of 3 different scheudling algorithms - namely First Come First Serve (FCFS), Round Robin (RR) and Dynamic Round Robin (DRR). The processes are created randomly and processed by Long-term scheduler, Medium-term scheduler and Short-term scheduler using Multithreading. The performance is compared on the basis of certain criteria and displayed using GUI (Graphical User Interface).
	
## Technologies
Project is created with:
* Software: Eclipse Java Oxygen
* Programming Language: JAVA
	
## Usage

Instantiate a `CPUScheduler` object 
```java
CPUScheduler fcfs = new FirstComeFirstServe();
```

Call the `Threads` class object passing all the scheduling algorithm objects
```java
Threads t1 = new Threads(fcfs, rr, drr)
t1.callThreads()
```

That will create three threads that execute simultaneously which namely are `makeProcess` , `longTermScheduler` and `shortTermScheduler` methods.  We can add a new `Row` for every job queued with random values.

```java
fcfs.add(new Row("P1", 0, 7));
fcfs.add(new Row("P2", 1, 3));
```

Call the `execute` method in `shortTermScheduler` method to process the respective algoirthm

```java
fcfs.execute();
```

Use the methods in respective java classes of algorithms to evaluate

```java
fcfs.getAverageTurnAroundTime();  
fcfs.getAverageWaitingTime();     
fcfs.getResponseTime();  
```

## Summary
This project primarily creates instances of all the algorithms present - that are - FCFS, RR, and DRR. Then, it creates 3 separate threads - for making processes, long term scheduler and short term scheduler. First thread makes process with random parameters assigned to it such as arrival time and burst time. The `makeProcess` method adds this process into new queue. Then, `longTermScheduler` method extracts the processes residing inside new queue and adds them into ready queue one by one. If the ready queue size is full indicating in shortage of memory available, it adds that process into ready suspend queue. Also, each time a process is extracted from new queue, first thread is notified to fill in other processes into new queue. The `shortTermScheduler` method waits till there is at least one entry in the ready queue and then processes all the algorithms according to the processes present. Now RR, FCFS, and DRR are called and starts processing. As soon as there is an empty space in the ready queue caused by removal by short terms scheduler, processes in the ready suspend queue are added in the ready queue by the medium term scheduler. After processing, it displays Average waiting time, Average Turn Around time, Average response time and number of context switches of each algorithm. Additionally, it displays waiting time, turn around time and response time for each process in all algorithms. 

## Results

##### Comparison between FCFS and RR with small time quantum 
RR performs better than FCFS 
![Alt Text](https://github.com/MuskanM1/CPU_Scheduler/blob/master/docs/Screenshots/1_FCFS_RR.JPG)

##### Comparison between FCFS and RR with big time quantum
FCFS and RR with big time quantum performs similar
![Alt Text](https://github.com/MuskanM1/CPU_Scheduler/blob/master/docs/Screenshots/2_FCFS_RR90.JPG)

##### Comparison between RR and DRR
DRR performs better than RR
![Alt Text](https://github.com/MuskanM1/CPU_Scheduler/blob/master/docs/Screenshots/3_RR_DRR.JPG)

##### Comparison between FCFS and DRR
DRR performs better than FCFS
![Alt Text](https://github.com/MuskanM1/CPU_Scheduler/blob/master/docs/Screenshots/4_FCFS_DRR.JPG)


## Report Link
https://drive.google.com/open?id=16BMRm3xcQWKWezno8RVzwSJd_2qD32Nz

