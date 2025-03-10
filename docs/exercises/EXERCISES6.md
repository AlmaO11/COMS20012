# Exercises sheet 6

**Correction around Easter.**

**Ask questions on [padlet](https://uob.padlet.org/sanjayrawat/2yrm4w4fh1osjzgt){:target="_blank"}!**

1. Explain in your own words why abstractions are necessary.

    **Answer:** they are there to make programming simpler. Without them user level program will have to understand the logic of every piece of hardware they may have to interact with. Abstractions also allow separation of concerns, the abstraction present an interface that hides away the logic of the "object" being abstracted. Abstractions also help with portability, indeed, as long as the same interface is presented to software building upon it, the underlying implementation/hardware should not matter.

2. Explain in your own the difference between policy and mechanism. How does this relate to abstractions?

    **Answer:** a policy is a sort of "contract" describing what an interface/piece of software should do, while the mechanism is the implementation effecting this policy.
3. Explain what piece of hardware thread, address space and files help to abstract.

    **Answer:** thread: CPU, address space: RAM, files: disk.
4. Processes are not tied to a specific piece of hardware. What is their role?

    **Answer:** they encapsulate other abstractions necessary for the execution of a task (i.e. thread, address space and files)
5. What are inter-process and intra-process communications?

    **Answer:** intra-process communication are achieved through the use of shared memory between the thread of a given process and synchronization primitives. Inter-process communications are used for interaction between different processes, they include pipes, sockets, message queues etc. You can get more explanations [here](https://tldp.org/LDP/tlk/ipc/ipc.html){:target="_blank"}
6. Explain [fork](https://man7.org/linux/man-pages/man2/fork.2.html){:target="_blank"} [exec](https://man7.org/linux/man-pages/man3/exec.3.html){:target="_blank"} [exit](https://man7.org/linux/man-pages/man3/exit.3.html){:target="_blank"} and [waitpid](https://man7.org/linux/man-pages/man2/waitid.2.html){:target="_blank"} system calls.

    **Answer:** fork: create a copy of the existing process; exec: replace the process image by a new image (typically loading a program stored on disk); exit: terminate the process; waitpid: suspend the calling process until the status of its child is available. The exact behaviour depends on the parameter being passed.
7. Explain the value return by the [open](https://man7.org/linux/man-pages/man2/open.2.html){:target="_blank"} system call.

    **Answer:** open return a file descriptor. This is the index corresponding to the opened file  in the process file table.
8. Explain why there are three different level of indirection between a user space process and file information on disk.

    **Answer:** they all fulfil different role. The object is to separate concerns and to share different states in a meaningful manner (e.g. access privilege should be system wide while the offset may be local to a process or a group of processes).
9. Explain in a few words what happens during a thread switch.

    **Answer:** outgoing thread register values are saved on the stack, stack is switched to that of incoming thread, incoming thread register values are loaded from its stack, incoming thread execution proceeds.
10. What is a delay slot in the MIPS architecture?

    **Answer:** in MIPS certain instructions are followed by a delay slot. An instruction executed during a delay slot does not see the effect of the instruction that precedes it.
11. What is batch scheduling?

    **Answer:** batch scheduling is when jobs/tasks are scheduled sequentially until they terminate.
12. What is time sharing?

    **Answer:** it is a type of scheduling where several processes are allowed to make progress concurrently.
13. Explain: thread switch, process switch and domain crossing.

    **Answer:** thread switch: change from one thread of execution to another, process switch: change from one process to another; domain switch: change the privilege level at which a process is executing (user -> kernel or kernel -> user).
14. What happened if you set a timer to switch between thread/process too often?

    **Answer:** if the timer used to trigger your scheduling logic is too short you will spend more time selecting the next thread to run and performing context switch than you would be making progress.
