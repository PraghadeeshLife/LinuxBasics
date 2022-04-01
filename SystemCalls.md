# System Calls and Device Drivers #

The real fun is when we interact with lower level system using System Calls, let's explore more about the System calls and Device Drivers here.
These functions called **system calls** provided by UNIX and Linux provides us with an interface to interact with the *Operating System*.

At the heart of the operating systems and at low level there are number of drivers called as **device drivers**, which facilates providing interaction with the hardware
layer, the device drivers are programmed to handle each device in a specific way because a device like tap driver needs to wind and locating the right spot to start
reading and writing whereas a device such as hard drive is a block device, which means it can accessed randomly but can be writted on on the free sector space.

The low level functions used to access **device drivers** are
  1. read
  2. write
  3. open
  4. close
  5. ioctl

The system calls are usually documented in the second section of the manual pages.

## Performance hits of System Calls ##
There are some performance hits while using System Calls, the programs should be designed in such a way to have the **least amount of System Calls**, to reduce the system
overhead switching from the user space to kernel space and switiching back to the normal state. Also, the system calls should try to read and write a block of data
directly rather than writing the data character by character which will consume a large amount of CPU Overhead, well this also is subjected to hardware limitations. Thus,
we say that the Library Function such Standard Input and Output are more efficient.

## Low Level File Access ##
We often use *file descriptors*, infact each process is associated with a file descriptor. The three file descriptors that are available are
  0: Standard Input
  1: Standard Output
  2: Standard Error
  
### write ###

### read ###

### open ###

### close ###
