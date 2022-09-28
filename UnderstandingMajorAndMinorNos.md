Understanding Major and Minor Numbders in Linux Device Drivers

Hello All, This is Praghadeesh and in this blog let's understand the use of Major Numbers and Minor Numbers and understand how we can allocate them statically
and dynamically while loading a module.

The character devices are accessed as normal files but they are called as special files or device files and found present under /dev directory.

![image](https://user-images.githubusercontent.com/102030901/192805194-29836e01-fea4-48d4-8feb-28e895526a4e.png)

As we can see in the above screenshot of ls -l /dev/ command output, we can see that the character devices are identified by the character "c" and the file looks
like a normal file

In the above screenshot, we will also be able to notice that there are two numbers that are seperated by comma present before the data, those numbers are called
as the major number and minor number in the given order.

The major number is used to identify a driver associated with it whereas a minor number is used by the driver to distinguish multiple devices associated with it,
it is not used by Kernel. Let's say we have a hard disk with four partitions present in it. Now the harddisk will have a Major number that is associated to the 
driver that is handling the hard disk and all the four different partitions are identified with minor numbers which will be used by the driver to distinguish.

Again as you can see in the above screenshot attached earlier, we can observer all the i2c-* devices are assoiated to only one driver identified by Major Numnber
89 and all the buses that are controlled by the driver are identified with unique minor numbers.

The below is an flowchart of how the device drivers and application communicate, so to reigister our device under /dev directory it is important for us to
use major number and minor numbers.

