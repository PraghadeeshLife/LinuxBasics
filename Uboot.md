Understanding U-boot

What is bootloader?

The boot loader is a piece of code that is executed when the hardware is turned on. In short, the boot loader is a piece of code that takes care of
initialization of important devices and peripherals.

In embedded systems, the bootloader initialized the important peripherals and loads the kernel onto RAM and hands over the control to Kernel.

What is u-boot?

U-boot is the most popular and open source boot loader that is typically used in Linux Based embedded systems. U-boot is both first stage and second stage
boot loader and it also provides the user with Command Line Interface, where the user can interact with hardware devices using the commands exposed by the
u-boot. We will be using this interface later to modify the Multiplexer configuration using this Command Line Interface. U-boot can also be provided with 
information such as device tree while loading the kerenle into OS. 

Device Tree can be considered as a hard description language, which descripes the hardwares and peripherals that are availble for the Kernel to make use of
and this can be modified for a specific SoC based on the use case.

What is the need for Pin Muxing?
In a typical SoC, due to the space constraints and limitations we have only few signals exposed as Pin which as generally decided by the Hardware
manufacturers, meaning a single pin may have multiple signals such as GPIO, I2C, SPI but only one can be used which is dictated by Hardware manufacturer
based on the perception of how the device might be used. The Pin Muxing helps us with the above limitation
and provide us with more flexibility which will
suit our use case. Let's say we require three I2C Buses for our use case, but we have only two I2C Buses that are default as per manufacturer in that case
we can look at the Technical Reference Manual of the SoC and modify the Multiplex in such as way to convert the default pins to a new I2C bus thus fulfilling
our use case.

The pin muxing can be done on the device tree or through the Command Line Interface exposed by the u-boot. 

In this blog, let's understand how pin multiplexing is done throught the Command Line Interface using u-boot.

We will be using TI's AM3358 SoC (BeagleBone Black Rev C) for the demonstration and this can be done by understanding the Technical Reference Manual.

Click to access the AM335x's Technical Reference Manual https://www.ti.com/lit/ug/spruh73q/spruh73q.pdf
Click here to see the Pin out and header of BeagleBone, the Mode 1 represents the default operation of that specific pin and other modes describe in which they can be modified as per the use case.

