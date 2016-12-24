# win-drivers-for-Galileo-Gen2
The Galileo Gen2 needs two serial device drivers to allow Windows to communicate with the programming port on the Galileo, most commonly when using the Arduino IDE to upload a sketch from the Windows PC to the Galileo. These drivers can be hard to find. They are placed here for convenience.

Issue: Intel's Galileo Gen2 card runs a version of Yocto Linux and is Arduino compatible. A limited version 
of Yacto is stored in flash memory.  A full version of Yacto is stored on a micro SD card. The Galileo card 
has a "programming" USB port (USB client) and requires two serial port drivers to allow it to 
communicate with a Windows PC, i.e., to upload Arduino sketches via the programming USB port. It 
needs one Windows serial port driver if the Galileo is booted using  the "flash" based Yacto.  and a 
different Windows serial port driver for the "SD card" based Yacto.

When the Galileo Gen2 boots initially using the "flash" based Yacto, Windows sees the USB 
programming port as "Gadget 2.4" serial device in Device Manager.

When the Galileo Gen2 boots initially using the "SD card" based Yacto, Windows sees the USB 
programming port as"CDC" serial device in Device Manager.

From Device Manager, by right clicking on the serial device, the Windows driver for it can be updated by 
browsing to the driver file on your PC. 

The Windows driver files for when the Galileo Gen2 boots initially using the "flash" based Yacto, and 
Windows sees the USB programming port as "Gadget 2.4" serial device in Device Manager are still 
found in a separate download file on Intel's Galileo support web site as of December 23, 2016 and are 
not a problem. They are included here for convenience.

The Windows driver files for when the Galileo Gen2 boots initially using the "SD card" based Yacto, and 
Windows sees the USB programming port as"CDC" serial device in Device Manager were a big 
problem for me. The drivers are described very carefully on Intel's support site for the Galileo as being 
included in the image file for the full version of Yacto that is provided for Galileo users to download and 
burn to a micro SD card. They are not there.

I found a reference in a months old forum post to an older image file that did have them, you can only see 
them in the file after you unzip the downloaded file and bun it to a micro SD card. I did and have included 
the files here for convenience.

Use these files at your own risk, I had no hand in making them, I just would like to spare someone else 
the frustration I had trying to make the Galileo Gen2 card work and provide enough information for 

someone to get the files the same way I did from Intel's Galileo support site.

The two "iot_devkit" files are the driver files for the "CDC" serial device (usin SD card Yocto) and the two "linux-cdc-acm" files are the driver files for the "Gadget 2.4" serial device (flash based Yocto). 

**************Some More Backgrounf Information*********************

Reference Intel Instructions:
https://software.intel.com/en-us/get-started-galileo-windows-step1

Following the instructions:
Getting Started with the Intel Galileo Board on Windows

This guide contains steps to set up your Intel Galileo board, including steps to setup a serial terminal, 
connect over Wi-Fi, and install your preferred integrated development environment (IDE) for general 
development in JavaScript, C/C++, or Python.

OS Requirements

The steps include instructions that are compatible with the following versions of the Windows operating 

system:

    Windows 7* 32/64
    Windows 8* 32/64
    Windows 8.1* 32/64

I am using Win 8.1 64 bit

Problem is at this step after writing the latest Yocto Image to the micro SD card, I have done it 3 times, I 

even upgraded to the latest Win32DiskImager in case my old version was the problem, no joy:

Method 2: Manual Process

Write the image to your micro SD card

Step 9

After completing the write process, click Exit to close Win32 Disk Imager. Once the write process is 
complete, your bootable micro SD card should contain the following:

o boot
o firmware
o win-driver
o bzImage

My image contains boot and bzimage and Yoocto works fine on the Galileo Gen2 however, the win-driver 
files and firmware files are missing. I don't need the firmware files but without the "win-driver" files I 
cannot upload sketches to the Galileo because Windows 8.1 cannot install drivers for the serial port 
used by the USB Client port on the Galileo. The port is recognized by Win 8.1 and shows up as "CDC" 
serial port in Device Manager, but drivers are not installed can't be found. This means I can't upload 
Arduino sketches to the Galileo when using the micro SD card.
