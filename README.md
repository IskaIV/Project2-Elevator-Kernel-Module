# **Project 2: Elevator Kernel Module**

## Description

- This project aims to provide us with a comprehensive understanding of system calls, kernel programming, concurrency, synchronization, and elevator scheduling algorithms. It consists of multiple parts that build upon each other to deepen our knowledge and skills in these areas.

- In Part 1, we start by working with system calls. By adding system calls to a C program and verifying their correctness using the “strace” tool, we gain hands-on experience with system call integration and learn about the available system calls for our machine. This part lays the foundation for understanding how system calls interact with the kernel.

- Part 2 takes us further into kernel programming. We will develop a kernel module called “my_timer” that retrieves and stores the current time using the “ktime_get_real_ts64()” function. This module creates a proc entry and allows us to read the current time and elapsed time since the last call. This part helps us understand how kernel modules work, how to interact with kernel functions, and how to use proc interfaces for communication.

- Part 3 focuses on a more complex task: implementing a scheduling algorithm for a dorm elevator. We create a kernel module representing the elevator, supporting operations like starting, stopping, and issuing requests. The module also provides a “/proc/elevator” entry to display important elevator information. This part challenges us to manage concurrency, synchronization, and efficient scheduling within the kernel environment.

- Each part of the project builds upon the knowledge and skills gained in the previous parts. Part 1 introduces us to system calls and their integration, which forms the basis for kernel programming in Part 2. Part 2 expands our understanding of kernel modules and communication through proc interfaces, setting the stage for the more advanced concepts explored in Part 3.

- By completing this project, we acquire practical experience in system calls, kernel programming, concurrency, synchronization, and scheduling algorithms. These are essential skills for developing efficient and robust software systems, particularly in operating systems and low-level programming domains. Understanding system calls and kernel programming enables us to interact with and extend the functionality of the operating system, while concurrency, synchronization, and scheduling concepts are crucial for efficient resource management and multitasking in complex systems.


## Group Members
1. **Souhail Marnaoui**:
  > sm22cb@fsu.edu
3. **Iskandar Verdiyev**:
  > iv22d@fsu.edu
5. **Panayoti Kourkoumelis**:
  > pk22j@fsu.edu

## Division of Labor
### Part 1: System-Call Tracing
**Details**:
- Follow the instructions below to complete the task:
 1. Create an empty C program named "empty".
 2. Make a copy of the "empty" program and name it "part1".
 3. Add exactly five system calls to the "part1" program. You can find the available system calls for your machine in "/usr/include/unistd.h".
 4. To verify that you have added the correct number of system calls, execute the following commands in the terminal:
  ```
  $ gcc -o empty empty.c
  $ strace -o empty.trace ./empty
  $ gcc -o part1 part1.c
  $ strace -o part1.trace ./part1
  ```

To minimize the length of the output from strace, try to minimize the use of other function calls (e.g., stdlib.h) in your program.

> [!NOTE]
> Running strace on an empty C program will generate a number of system calls. Therefore, when using strace on your Part 1 code, it should produce five more system calls than the empty program.

**Assigned to**:
> Souhail Marnaoui, Iskandar Verdiyev


### Part 2:  Timer Kernel Module
**Details**:
- In Unix-like operating systems, the time is often represented as the number of seconds since the Unix Epoch (January 1st, 1970). The task requires creating a kernel module named `my_timer` that utilizes the function `ktime_get_real_ts64()` to retrieve the time value, which includes seconds and nanoseconds since the Epoch.
 1. Develop a kernel module called my_timer that calls the `ktime_get_real_ts64()` function to obtain the current time. This module should store the time value.
 2. When the `my_timer` module is loaded using `insmod`, it should create a proc entry named `/proc/timer`.
 3. When the `my_timer` module is unloaded using `rmmod`, the `/proc/timer` entry should be removed.
 4. On each read operation of `/proc/timer`, utilize the proc interface to print both the current time and the elapsed time since the last call (if valid).

- To insert a kernel module:
  ```$ sudo insmod my_timer.ko```
- To remove a kernel module:
  ```$ sudo rmmod my_timer.ko```
- To check for your kernel module:
  ```$ lsmod | grep my_timer```
- Example Usage:
  ```
  $ cat /proc/timer
  current time: 1518647111.760933999
  
  $ sleep 1
  
  $ cat /proc/timer
  current time: 1518647112.768429998
  elapsed time: 1.007495999
  
  $ sleep 3
  
  $ cat /proc/timer
  current time: 1518647115.774925999
  elapsed time: 3.006496001
  
  $ sleep 5
  
  $ cat /proc/timer
  current time: 1518647120.780421999
  elapsed time: 5.005496000
  ```

**Assigned to**:
> Souhail Marnaoui, Panayoti Kourkoumelis


### Part 3a: Adding System Calls
**Details**:
This part requires us to implement a scheduling algorithm for a office elevator. You will create a kernel module elevator to implement this.

**Assigned to**:
> Iskandar Verdiyev, Panayoti Kourkoumelis


### Part 3b:  Kernel Compilation
**Details**:

**Assigned to**:
> Souhail Marnaoui, Panayoti Kourkoumelis


### Part 3c: Threads
**Details**:

**Assigned to**:
> Souhail Marnaoui, Iskandar Verdiyev


### Part 3d: Linked List
**Details**:

**Assigned to**:
> Iskandar Verdiyev, Panayoti Kourkoumelis


### Part 3e: Mutexes
**Details**:

**Assigned to**:
> Souhail Marnaoui, Panayoti Kourkoumelis


### Part 3f: Scheduling Algorithm
**Details**:

**Assigned to**:
> Souhail Marnaoui, Iskandar Verdiyev, Panayoti Kourkoumelis


> [!NOTE]
> Please note that these assignments are subject to discussion and adjustment based on the team's
agreement and individual expertise. Regular communication and collaboration among team
members are encouraged to ensure the successful completion of the project**

## File Listing
```
root/
├── bin/           -- executable
├── include/       -- header files
├── obj/           -- object files
├── src/           -- source files
├── Makefile
└── README.md
```
## How to Compile & Execute

### Requirements
- **Compiler**: e.g., `gcc` for C/C++, `rustc` for Rust.
- **Dependencies**: List any libraries or frameworks necessary (rust only).

### Compilation
For a C/C++ example:
```bash
make
```
This will build the executable in ...
### Execution
```bash
make run
```
This will run the program ...

## Bugs
- No known bugs :)
