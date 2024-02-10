# Task 3 - Analyze the Firmware - (Emulation)

Leveraging that datasheet enabled you to provide the correct pins and values to properly communicate with the device over UART. Because of this we were able to communicate with the device console and initiate a filesystem dump.

To begin analysis, we loaded the firmware in an analysis tool. The kernel looks to be encrypted, but we found a second-stage bootloader that loads it. The decryption must be happening in this bootloader. There also appears to be a second UART, but we don't see any data coming from it.

Can you find the secret key it uses to decrypt the kernel?

Tips:
You can emulate the loader using the provided QEMU docker container. 
One download provides the source to build your own. 
The other is a pre-built docker image. 
See the README.md from the source download for steps on running it.
Device tree files can be compiled and decompiled with dtc.

Downloads:
U-Boot program loader binary (u-boot.bin)
Recovered Device tree blob file (device_tree.dtb)
Docker source files to build the QEMU/aarch64 image (cbc_qemu_aarch64-source.tar.bz2)
Docker image for QEMU running aarch64 binaries (cbc_qemu_aarch64-image.tar.bz2)

Open u-boot.bin in Ghidra analyze the binary disassembled ARM assembly
find function handling cryptographic key
Install dtc sudo apt-get install dtc
dtc -I dts -O dtb -o  
```
sudo docker run -it --rm --device=/dev/net/tun:/dev/net/tun --cap-add NET_ADMIN -v $(pwd)/myfiles:/myfiles cbc_qemu_aarch64:latest
sudo docker ps | grep cbc_qemu_aarch64:latest
sudo docker exec -it <CONTAINER ID> /bin/bash

# window 1
nc -l 10000

# window 2
nc -l 10001

export UBOOT=/myfiles/u-boot.bin
export DTB=/myfiles/device_tree.dtb

qemu-system-aarch64 -M virt,secure=on -cpu cortex-a53 -bios /myfiles/u-boot.bin -dtb /myfiles/device_tree.dtb -display none -chardev socket,host=localhost,port=10000,id=uart0 -chardev socket,host=localhost,port=10001,id=uart1 -serial chardev:uart0 -serial chardev:uart1
```
