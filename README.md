# Project Overview

## Description
This project implements a simple process scheduler and manager, along with a basic shell interface for submitting commands to be executed. The scheduler employs a round-robin scheduling algorithm to manage processes, ensuring fair allocation of CPU time among submitted tasks.

## Use Cases
- **Process Management:** Users can submit commands to the scheduler, which creates child processes to execute these commands.
- **Fair CPU Allocation:** The scheduler ensures that each process receives a fair share of CPU time through round-robin scheduling, preventing any single process from monopolizing resources.
- **Shell Interface:** The shell interface allows users to interact with the scheduler, submitting commands for execution and receiving feedback on process completion.

## Implementation
- **Shared Memory:** Shared memory is used to facilitate communication and synchronization between the scheduler process and child processes.
- **Semaphore:** Semaphores are utilized to control access to shared resources and ensure thread-safe operations, particularly in the enqueue and dequeue operations of the process queue.
- **Signal Handling:** Signals such as SIGSTOP and SIGCONT are employed to pause and resume execution of child processes, allowing the scheduler to control the flow of execution.

## Scope
- **Process Scheduling:** The scheduler employs a round-robin algorithm to manage processes, ensuring fair allocation of CPU time among submitted tasks.
- **Basic Shell Interface:** The shell interface provides a simple command-line interface for users to submit commands for execution.
- **Limited Process Management:** While the project supports basic process management functionalities such as submission and execution, it does not include advanced features such as process priority management or resource allocation.
- **Single Host Execution:** The project is designed to run on a single host system, managing processes within the system's resources. It does not support distributed computing or multi-host environments.
