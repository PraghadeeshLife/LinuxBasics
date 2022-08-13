# Understanding the System Calls and adding our own system call to the linux kernel #

System Call is something that you would be well aware of, if you are from Linux System Programming background. In this blog, let's try to understand the working of system call in the process of implementing our own system call. 

An operating system can be classified into two
1. User Space - Where almost all the user space and high level applications run
2. Kernel Space - A privelaged and secured space used by the Operating System

System call is just like an API exposed to toggle between user space and kernel space from user space programs. System calls may look like anyother normal function call that takes arguments but in a sense they are more than that the System calls are function invocations made from user space program to request any service or resources from the operating system.

Linux implements a far fewer system calls in the range of 300, compared to thousands of system calls in operating systems such as Windows.

So, basically here are some point on the system call
1. A system call switches the processor from user mode to kernel mode, making it possible to access the protected Kernel Memory
2. There are only set of specific number of system calls and they are identified by the System call name. Each system call has a unique number assigned to it. The list of registered system calls are maintained in the system call table.
3. System call consists of arguments that contains the data to be transferred between User space and Kernel Space and Vice Versa.

Here are some of the common system calls used and their unique numbers assigned for the x86 architecture, these can be found listed at the following path /usr/include/asm/unistd.h. The system call number varies with respect to architecture.

```
#define __NR_exit                 1
#define __NR_fork                 2
#define __NR_read                 3
#define __NR_write                4
#define __NR_open                 5
#define __NR_close                6
#define __NR_waitpid              7
#define __NR_creat                8
#define __NR_link                 9
#define __NR_unlink              10
#define __NR_execve              11
#define __NR_chdir               12
#define __NR_time                13
#define __NR_mknod               14
#define __NR_chmod               15
#define __NR_lchown              16
```

Let's explore the behind the scenes actions that takes place when an application invokes a system call
1. When an user space function invokes a System call, the wrapper library function for the system call is called.
2. The wrapper function must make available all the arguments passed to the system call to be used by the trap and handler routine. The arguments are passed to the wrapper function through stack but since kernel expects them in specific registers, these arguments are copied to specific register in which the Kernel can access them.
3. All the system calls enter the kernel in the same way, so in order to identify the system call they are identified by the system call number which is copied to the register %eax ans will be used by the kernel.
4. Once the system call number is copied to the kernel, the wrapper function then executes a trap machine instruction int 0x80 which causes the processor to enter the kernel realm. 
5. Following the trap instruction, the kernel executes a software interrupt handler which is the system call handler located at arch/i386/entry.S to handle the trap. The handler then goes through the following flow.
- Copies the arguments and system call number from register onto Kernel Stack
- Executes the system call routine identified based on the unique number assigned to it from the sys_call_table and returns the result status to the system_call() routine.
- Restores the values onto register from kernel stack and places the system call return value on the stack.
- Returns to the wrapper function and to the user mode.

![image](https://user-images.githubusercontent.com/102030901/184476835-ed44e61d-75f8-4239-b9b4-532090ab242d.png)

The above illustrates the flow of what happens when execve system call is invoked from the user space application. As we can see, the glibc wrapper function is called when the system call is encountered in user space program, where the wrapper function's implementation of execve copies the arguments and system call numbers onto registers and executes the int 0x80 instruction which make it enter into Kernel Space and calls the trap handler which subsequently calls the specific execve system call routine from the sys_call_table and finally returns back to the user mode and the success/ failure status of the system call is passed to the wrapper function.

Hence, the above is the behind the scenes working of System Calls. 

Thanks for reading!

References Used:
1. Linux System Programming by Robert Love
2. The Linux Programming Interface by Michael Kerrisk
