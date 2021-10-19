# synchronization-tools


 Chapter 6 Synchronization Tools:

CHAPTER OBJECTIVES 

• Describe the critical-section problem and illustrate a race condition.

 • Illustrate hardware solutions to the critical-section problem using memory barriers, compare-and-swap operations, and atomic variables.

 • Demonstrate how mutex locks, semaphores, monitors, and condition variables can be used to solve the critical-section problem. 

• Evaluate tools that solve the critical-section problem in low-, moderate-, and high-contention scenarios


















Cooperating process/ cooperating process is one that can affect or be affected by other processes executing in the system.

race condition/ A situation like this, where several processes access and manipulate the same data concurrently and the outcome of the execution depends on the particular order in which the access takes place, is called a race condition

process synchronization and coordination/ multicore systems are using multithreaded application. In such applications, several threads—which are quite possibly sharing data—are running in parallel on different processing cores. Clearly, we want any changes that result from such activities not to interfere with one another, that's why we use synchronization.

critical section/ Each process has a segment of code, called a critical section, in which the process may be accessing — and updating — data that is shared with at least one other process.

entry section / The section of code implementing this request is the entry section.

exit section/ The critical section may be followed by an exit section.

remainder section/ The remaining code is the remainder section











two general approaches are used to handle critical sections in operating systems:

preemptive kernels/ allows a process to be preempted while it is running in kernel mode.

nonpreemptive kernels/ A nonpreemptive kernel does not allow a process running in kernel mode to be preempted; a kernel-mode process will run until it exits kernel mode, blocks, or voluntarily yields control of the CPU.

Peterson’s solution/ next, we illustrate a classic software-based solution to the critical-section problem known as Peterson’s solution. Because of the way modern computer architectures perform basic machine-language instructions, such as load and store, there are no guarantees that Peterson’s solution will work correctly on such architectures. However, we present the solution because it provides a good algorithmic description of solving the critical-section problem and illustrates some of the complexities involved in designing software that addresses the requirements of mutual exclusion, progress, and bounded waiting.

memory model/ How a computer architecture determines what memory guarantees it will provide to an application program is known as its memory model.

memory barriers or memory fences / computer architectures provide instructions that can force any changes in memory to be propagated to threads running on other processors.

atomically/ many modern computer systems provide special hardware instructions that allow us either to test and modify the content of a word or to swap the contents of two words atomically

atomic variable/ One such tool is an atomic variable, which provides atomic operations on basic data types such as integers and booleans.

mutex lock/ Instead, operating-system designers build higher-level software tools to solve the critical-section problem. The simplest of these tools is the mutex lock.




contended/ if a thread blocks while trying to acquire the lock.
uncontended/ If a lock is available when a thread attempts to acquire it, the lock is considered uncontended.

busy waiting/ the main disadvantage of the implementation given here is that it requires busy waiting.

spinlock/ The type of mutex lock we have been describing is also called a spinlock because the process “spins” while waiting for the lock to become available.

semaphore/ A semaphore S is an integer variable that, apart from initialization, is accessed only through two standard atomic operations: 
wait() and signal().

counting semaphore/ can range over an unrestricted domain.

binary semaphore/ can range only between 0 and 1. Thus, binary semaphores behave similarly to mutex locks.

monitor/ One strategy for dealing with such errors is to incorporate simple synchronization tools as high-level language constructs. In this section, we describe one fundamental high-level synchronization construct— the monitor type.

abstract data type – ADT/ ADT—encapsulates data with a set of functions to operate on that data that are independent of any specific implementation of the ADT. A monitor type is an ADT that includes a set of programmer-defined operations that are provided with mutual exclusion within the monitor.

conditional-wait/ In many circumstances, however, such a simple scheduling scheme is not adequate. In these circumstances, the conditionalwait construct can be used. This construct has the form
 x.wait(c);


priority number/ The value of c, which is called a priority number


Liveness/ refers to a set of properties that a system must satisfy to ensure that processes make progress during their execution life cycle.


Deadlocked/ The event in question is the execution of a signal() operation. When such a state is reached, these processes are said to be deadlocked.

priority inversion/ when we have serval processes that have certain piretites, hence when a process requires a semaphore that is accessed by other process, hence the other process waits, hence the process with a lower priority has affected how long the other process must wait for 1st process to relinquish resource, hence it creates a liveness problem

 
a priority-inheritance protocol. / Typically, priority inversion is avoided by implementing a priority-inheritance protocol. 
lock-free/ algorithms that provide protection from race conditions without requiring the overhead of locking.












