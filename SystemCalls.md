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

The system calls are usually documented in the second section of the manual pages/man pages.

The library related details are usually documented in the third section of the manual pages/man pages.

## Performance hits of System Calls ##
There are some performance hits while using System Calls, the programs should be designed in such a way to have the **least amount of System Calls**, to reduce the system
overhead switching from the user space to kernel space and switiching back to the normal state. Also, the system calls should try to read and write a block of data
directly rather than writing the data character by character which will consume a large amount of CPU Overhead, well this also is subjected to hardware limitations. Thus,
we say that the Library Function such Standard Input and Output are more efficient.

## Low Level File Access ##
We often use *file descriptors*, infact each process is associated with a file descriptor. The three file descriptors that are available are
  0. Standard Input
  1. Standard Output
  2. Standard Error
  
### write ###
The write system call writes the first nbytes arranged in the buffer to be written with the file associated with the file descriptor. It returns the number of bytes wirtten, if the write action is successful, 0 if nothing is written and -1 if there are any failures.

```
#include <unistd.h>
size_t write(int fd, const void *buf, size_t nbytes);
```

### read ###
The read system call reads the first nbytes from the buffer from the file associated with the file descriptor. It returns the number of bytes read, which could be lesser than nbytes and returns 0 if nothing is read or -1 if there are any failures.

```
#include <unistd.h>
size_t read(int fd, void *buf, size_t nbytes);
```

### open ###
The open establishes access to a path or a file and provides us with a file descriptor that can be used to access the read and write files. The file descriptor is unique and isn't the same for different processes running.

```
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
int open(const char *path, int oflags);
int open(const char *path, int oflags, mode_t mode);
```

The oflags are specified as a combination of mandotory file access mode and other optional modes. The open call must specify any one of the file flags shown below
O_RDONLY  | Open for read-only
O_WRONLY  | Open for write-only
O_RDWR    | Open for reading and writing

The **mode** is usually used only when the flag is set as O_CREAT or as O_TEMP, the other times it is usually ignored.  

### close ###
It returns 0 if succesfull and -1 is it is a failure.

```
#include <unistd.h>
int close(int fildes);
```

### ioctl ###
ioctl helps us to interact with the devices. More about this to be updated.

```
#include <unistd.h>
int ioctl(int fildes, int cmd, ...);
```
