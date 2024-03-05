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
**Instructions**:
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


- The user will be greeted with a prompt that should indicate the absolute working directory, the user name, and the machine name. This is done by expanding the `$USER, $MACHINE, $PWD` environment variables. The user will type on the same line as the prompt.
```
USER@MACHINE:PWD>
```
- Here is an example:
```
mnguyen@linprog2.cs.fsu.edu:/home/grads/mnguyen>
```
**Assigned to**:
> Souhail Marnaoui, Iskandar Verdiyev, Panayoti Kourkoumelis

### Part 2: Environment Variables
**Responsibilities**:
- In the context of program execution within its environment, you will replace tokens prefixed with the dollar sign character (`$`) with their corresponding values. Within the bash shell, you can utilize the `env` command to display a comprehensive list of your environmental variables. Your objective is to implement a mechanism that automatically expands tokens starting with the dollar sign into their respective values.
- For instance, given the command `echo, $USER`, the token `$USER` should be expanded to its corresponding value, resulting in the output `echo`, `mnguyen`. This expansion applies universally to any command, ensuring consistent token replacement throughout the shell. To accomplish this, you can utilize the `getenv()` function, the usage details of which can be found on its man page.
- It's important to note that this token expansion occurs regardless of the executed command, providing a seamless integration of environment variable values within commands and generating the expected output.

**Assigned to**:
> Souhail Marnaoui, Iskandar Verdiyev

### Part 3: Tilde Expansion
**Responsibilities**:
- In Bash, tilde (~) may appear at the beginning of a path, and it expands to the environment variable `$HOME`. For example, tokens `ls`, `~/dir1` should expand to `ls`, `/home/grads/mnguyen/dir1`. An output example of tilde expansion is:
```
~ → /home/grads/mnguyen
```
- You will only have to handle the tilde expansion of a token if `~` a standalone or if it begins with `~/`.

**Assigned to**:
> Souhail Marnaoui, Panayoti Kourkoumelis

### Part 4: $PATH Search
**Responsibilities**:
- In Bash, when a command like `ls` is entered, the shell is able to execute the corresponding program/executable located at `/usr/bin/ls` through a process called path search. This path search is not magical, but rather a straightforward search conducted within a predefined list of directories. The list of directories is specified in the environment variable `$PATH`.
- For commands that do not include a slash (/) and are not built-in functions (covered in part 9), it becomes necessary to search each directory specified in `$PATH`. It's important to note that `$PATH` is a string containing multiple directories delimited by a colon.
- To perform the search, you will need to employ string operations to extract and examine each directory in the `$PATH` variable.
- If you type in the command `echo $PATH` in your terminal you should get something like this:
```
/home/grads/mnguyen/.bin:/home/grads/mnguyen/.scripts:/usr/local/bin:/opt/sfw/bin:/usr/sfw/bin:/bin:/usr/bin:/usr/ccs/bin:/usr/ucb:.
```
- In the event that the command is not found in any of the directories listed in `$PATH`, an error message should be displayed. In Bash, this typically results in the familiar `command not found` error message. Handling this scenario involves proper error detection and reporting, ensuring a clear indication when a command is not available within the directories specified in `$PATH`.

**Assigned to**:
> Souhail Marnaoui

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
