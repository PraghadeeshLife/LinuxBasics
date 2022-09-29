Hello all, This is Praghadeesh and in this block let's understand the Embedded Linux Boot Process.

What is a bootloader?
In Simple terms, the boot loader is the first piece of the code that runs when a device is turned on and sets up the peripherals before the control is relinquished to
the operating system. A bootloader may also be called as bootstrap loader.

Here is the flow in which the Linux is booted in the embedded systems

![image](https://user-images.githubusercontent.com/102030901/192956031-1019b53f-f944-48ce-9b34-57ed910ef193.png)


Boot ROM or ROM Boot Loader
The first step of Booting is handled by the ROM Boot loader, which is a bootloader that is responsible for initializing CPU, Memory COntroller, On-Chip devices and configures memory map and loads the Secondary Program Loader into the Internal Memory or SRAM. The ROM Bootloader is set up by the manufacturer and can't be modified. The ROM bootloader can be configured to load SPL from MMC or UART or SD Card by configuring the SYSBOOT Register. The ROM bootloader will also configure the internal watchdog timer and configure the clock rate to a conservative fixed rate. The ROM Boot loader checks if the SPL Image is valid and loads into SRAM.

A ROM Boot loader requires
1. A Power Source
2. A Valid Clock Input
3. Bootmode Pin Selection

SPL
In some cases the u-boot is too large to be loaded into the Internal Memory or SRAM, in such cases a Secondary Program Loader is needed. The SPL then loads the u-boot into external memory or DRAM. The internal clocking rate is reconfigured by the SPL and in the absence of SPL by u-boot. Since, there is a memory limitation in the internal memory an SPL in this case a MLO file is first loaded into SRAM which will initialize the DRAM and copy the u-boot from MMC or SD Card into the DRAM. SPL sets up clocks (MPU, Core and Peripherals). 

U-Boot
The SPL after loading the u-boot into RAM, the following steps takes place. U-boot initializes any interfaces that are required which will help loading in Kernel. At the end u-boot copies the Kernel into the DRAM and hands over the control to Kernel. The u-boot also provides the Kernel with device tree and RAM Disk images. The u-boot also let's us to do board specific changes such as enabling or disabling a peripheral by pin muxing the registers associated with it. 

Kernel 
Once the Kernel is loaded into the memory, the initrd image is loaded and acts as a temporary root file system. Finally once all the drivers and kernel is loaded into memory and kernel is mounted with the root file system, it starts the first process called init.

Init
init is the first process started by the kernel, which will have a Process Identification Number (PID) as 1 and will serve as the parent for all other processes. And all other services are initialized consequently.

The above is the process in which the Embedded Linux Boots.

References:
1. TI's Training Video on Porting Linux in different Hardwares
2. Bootlin's Linux Booting Process

I hope you had a good read and gained something valuable out of it!

Subscribe and stay tune for more such content!

Thanks! 💻
