# Project Overview

## Description
This project implements a simple process scheduler and manager, along with a basic shell interface for submitting commands to be executed. The scheduler employs a round-robin scheduling algorithm to manage processes, ensuring fair allocation of CPU time among submitted tasks


## Use Cases
- **Process Scheduling:** SimpleScheduler schedules processes using a round-robin algorithm, ensuring fair CPU allocation.
- **Command-Line Interface:** Users interact with SimpleScheduler through a command-line interface provided by SimpleShell, submitting executables for execution.
- **Submission of Jobs:** Users can submit jobs using the "submit" command, specifying the executable to be run.
- **Limited CPU Resources:** SimpleScheduler manages a limited number of CPU resources, specified by the user during launch.
- **Termination:** SimpleShell and SimpleScheduler terminate upon user termination, with SimpleScheduler terminating only after all submitted jobs have completed.

## Implementation Details
### Basic Functionalities
1. **Initialization:** Users start SimpleShell, providing the total number of CPU resources (NCPU) and the time quantum (TSLICE) as command-line parameters.
2. **Command Prompt:** SimpleShell operates in an infinite loop, displaying a command prompt where users can submit executables for execution.
3. **Job Submission:** Users submit jobs using the "submit" command, creating a new process to run the specified executable.
4. **Signal Handling:** Upon creation, processes wait for a signal from SimpleScheduler before starting execution.
5. **SimpleScheduler Daemon:** SimpleScheduler is a daemon employed by SimpleShell for CPU scheduling activities, utilizing minimal CPU cycles.
6. **Ready Queue Management:** SimpleScheduler maintains a ready queue of processes ready for execution, scheduling processes in a round-robin fashion.
7. **CPU Scheduling:** SimpleScheduler selects NCPU processes from the front of the ready queue and signals them to start running. After TSLICE expires, it signals the running processes to stop execution and adds them back to the ready queue.
8. **New Job Scheduling:** If new processes arrive while others are running, they are scheduled from the next TSLICE onwards.
9. **Continued Job Submission:** Users can submit any number of jobs at any given time during the execution.
10. **Termination:** Termination of SimpleShell also terminates SimpleScheduler. SimpleScheduler terminates only after all submitted jobs have naturally completed.
11. **Job Reporting:** Upon termination, SimpleShell prints the name, PID, execution time, and wait time of all submitted jobs.

### Details
- **Shared Memory:** Shared memory is used to facilitate communication and synchronization between the scheduler process and child processes.
- **Semaphore:** Semaphores are utilized to control access to shared resources and ensure thread-safe operations, particularly in the enqueue and dequeue operations of the process queue.
- **Signal Handling:** Signals such as SIGSTOP and SIGCONT are employed to pause and resume execution of child processes, allowing the scheduler to control the flow of execution.

## Scope
- **Process Scheduling:** The scheduler employs a round-robin algorithm to manage processes, ensuring fair allocation of CPU time among submitted tasks.
- **Basic Shell Interface:** The shell interface provides a simple command-line interface for users to submit commands for execution.
- **Limited Process Management:** While the project supports basic process management functionalities such as submission and execution, it does not include advanced features such as process priority management or resource allocation.
- **Single Host Execution:** The project is designed to run on a single host system, managing processes within the system's resources. It does not support distributed computing or multi-host environments.
