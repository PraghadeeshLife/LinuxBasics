# Adding your own System Call #

Let's start by downloading the stable Linux Kernel

And then extract the kernel

![image](https://user-images.githubusercontent.com/102030901/184527551-bfa297f0-23a4-4492-9648-d00a19118f53.png)


Creating a directory under the Kernel directory
I am naming it as our_own_system_call

![image](https://user-images.githubusercontent.com/102030901/184527564-7cd2a516-7bd0-4ccf-a5e9-d47dae4a4372.png)
![image](https://user-images.githubusercontent.com/102030901/184529518-9fceb531-0ada-4144-a9f3-a785b97b4ac4.png)


cd into our_own_system_call directory and create our_own_system_call.c file

![image](https://user-images.githubusercontent.com/102030901/184527879-601589ea-6304-463e-b7d6-a5fdcc5fdbae.png)

create a Makefile

![image](https://user-images.githubusercontent.com/102030901/184528146-e513daab-50cf-4de6-b12d-79e85481b3ab.png)

![image](https://user-images.githubusercontent.com/102030901/184528361-e205adea-f426-4c98-8b10-46b8a01a0e5c.png)

Adding the new system call to the System call table
![image](https://user-images.githubusercontent.com/102030901/184530362-c8cceb55-f486-4992-b062-cff459de32a6.png)

![image](https://user-images.githubusercontent.com/102030901/184528831-caa7515d-ebf1-4d0f-b571-25c9638c5cea.png)


Adding the System Call in header file
![image](https://user-images.githubusercontent.com/102030901/184529454-7df83c7a-e32d-41d0-89f9-0d0cac26a18f.png)

Running sudo make menuconfig
![image](https://user-images.githubusercontent.com/102030901/184529863-5f7b11e5-7a69-4040-a809-d29a25f2664d.png)

Running make -j`nproc`
![image](https://user-images.githubusercontent.com/102030901/184529982-a7adcb1f-55e9-43e0-8dd2-7faf55f577e3.png)

