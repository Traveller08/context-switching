# Context Switching and Round Robin Scheduling

This project focuses on implementing Context Switching and Round Robin (RR) scheduling. Context Switching is essential when a process switch occurs to save and reload the process's state. In RR scheduling, the CPU time is divided into fixed time slices (quantum), and when a time slice is completed, the processor is allocated to the next process. Context Switching is crucial for smoothly transitioning between processes and ensuring they resume execution from where they left off. Context switching is implemented for both scheduling and I/O interrupts.

## OS Concepts Used
- **Five-state Model:** The project employs a five-state model (Blocked, Running, and Ready) to manage processes. Blocked and Ready states are implemented using queues. The Ready Queue is implemented as a circular queue to keep processes in a ready state until they terminate or complete their execution. When a process encounters an I/O interrupt, it is dequeued from the Ready Queue and enqueued into the Blocked Queue. Running state is not a queue because only one process can run at a time. When a resource becomes available, it is removed from the Blocked Queue and enqueued into the Ready Queue.

- **Scheduling:** Short-term scheduling is used to manage the Ready Queue. The Round Robin (RR) algorithm is chosen as the scheduling algorithm with a quantum of 2. RR scheduling ensures fair treatment for all processes and minimizes the risk of starvation. Additionally, RR is suitable for processes with shorter execution times.

- **Context Switching:** Context switching is implemented to ensure that when a process is allocated the CPU again, it starts execution from where it left off. This is achieved through the Process Control Block (PCB), which contains crucial information about the process, including the PID, state, Program Counter (PC), and Stack Pointer (SP).

##Implementation
The implementation involves the following components:

- **Main.c:** This file contains all operations, including process creation, scheduling, context switching, updating PCB, and the graphical user interface (GUI), implemented using GTK.

- **stack implementation.c:** It contains the implementation of a stack, including push and pop operations.

- **queue implementation.c:** This file contains the implementation of a queue, including enqueue and dequeue operations.

- **process*.txt:** These files contain instructions for each process.

## Running the Code
This code is designed to run on Linux. To execute it, follow these steps:

1. Compile the code:
   ```bash
   gcc `pkg-config gtk+-3.0 --cflags` main.c stack implementation.c queue implementation.c -o os `pkg-config gtk+-3.0 --libs`

 
