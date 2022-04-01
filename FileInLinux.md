# Files in Linux

As we know that in Linux almost everything is a **file**, one can read and write all the devices as one do for the file except some exceptions such as network devices.

The **five common system calls** that we use to handle files in system are,
  1. read
  2. write
  3. open
  4. close
  5. ioctl
  
The properties of the files are stored in something called **inode**, which contains details such as type of file, modified date and time, where it is located in the
directory and more details such as size, user permission, etc..

**A Directory** is a file that contains the inode numbers of the other files. Each directory entry is a link to file's inode, remove the file name and you can remove the
link.

## File Structure in Linux ##
  1. / - The Root
  2. /home - The home directory
  3. /bin - System Binaries
  4. /etc - System Configuration Files
  5. /lib - System Libraries
  6. /dev - Files that represent physical devices
  
# Files and Devices #
In Linux, even the CD ROM can be mounted directly as a file and can be accessed as file. Interesting!

There are three important device files found in both UNIX and Linux
### /dev/console ###
This device represents the system console, error messages and diagonostics are often sent to this console.

### /dev/tty ###
This device is used to control the terminal (monitor, keyboard, etc..). There is only one /dev/console but there are many /dev/tty device files.

### /dev/null ###
The /dev/null, throws an immediate EOF when the file is read and this is often used to put some unwanted output into this and emptied.
