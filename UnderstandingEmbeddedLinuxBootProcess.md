Hello all, This is Praghadeesh and in this block let's understand the Embedded Linux Boot Process.

What is a bootloader?
In Simple terms, the boot loader is the first piece of the code that runs when a device is turned on and sets up the peripherals before the control is relinquished to
the operating system. A bootloader may also be called as bootstrap loader.

Here is the flow in which the Linux is booted in the embedded systems
ROM -> SPL -> UBOOT -> KERNEL -> INIT

