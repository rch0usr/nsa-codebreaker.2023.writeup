# Task 4 - Emulate the Firmware - (Dynamic Reverse Engineering, Cryptography)
We were able to extract the device firmware, however there isn't much visible on it. 
All the important software might be protected by another method.

There is another disk on a USB device with an interesting file that looks to be an encrypted filesystem. 
Can you figure out how the system decrypts and mounts it? 
Recover the password used to decrypt it.
You can emulate the device using the QEMU docker container from task 3.

Downloads:
main SD card image (sd.img.bz2)
USB drive image (usb.img.bz2)
Linux kernel (kernel8.img.bz2)
Device tree blob file for emulation (bcm2710-rpi-3-b-plus.dtb.bz2)

