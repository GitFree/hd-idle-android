hd-idle-android
===============

This is a "version" with android support from Christian Mueller's hd-idle(http://hd-idle.sourceforge.net/).
>hd-idle is a utility program for spinning-down external disks after a period of idle time. Since most external IDE disk enclosures don't support setting the IDE idle timer, a program like hd-idle is required to spin down idle disks automatically.

>A word of caution: hard disks don't like spinning up too often. Laptop disks are more robust in this respect than desktop disks but if you set your disks to spin down after a few seconds you may damage the disk over time due to the stress the spin-up causes on the spindle motor and bearings. It seems that manufacturers recommend a minimum idle time of 3-5 minutes, the default in hd-idle is 10 minutes.

>One more word of caution: hd-idle will spin down any disk accessible via the SCSI layer (USB, IEEE1394, ...) but it will not work with real SCSI disks because they don't spin up automatically. Thus it's not called scsi-idle and I don't recommend using it on a real SCSI system unless you have a kernel patch that automatically starts the SCSI disks after receiving a sense buffer indicating the disk has been stopped. Without such a patch, real SCSI disks won't start again and you can as well pull the plug.

build hd-idle for android platform
===========================================
1.prepare common android build toolchain
----------------------------------------
    cd /home/gitfree/test
    wget https://sourcery.mentor.com/sgpp/lite/arm/portal/package3397/public/arm-none-linux-gnueabi/arm-2008q3-41-arm-none-linux-gnueabi-i686-pc-linux-gnu.tar.bz2
    tar vxf arm-2008q3-41-arm-none-linux-gnueabi-i686-pc-linux-gnu.tar.bz2
    export PATH=/home/gitfree/test/arm-2008q3/bin:$PATH
2.build hd-idle
----------------------------------------
    arm-none-linux-gnueabi-gcc -static hd-idle.c -o hd-idle
the output hd-idle is the executable file.Copy it to your android device.

Usage Document
==============
1.debug mode

    hd-idle -d
2.example

    hd-idle -a sda -i 300
    
This example will spin down device sda if it idles for 300 seconds.

    hd-idle -i 0 -a sda -i 300 -a sdb -i 1200
This example sets the default idle time to 0 (meaning hd-idle will never try to spin down a disk), then sets explicit idle times for disks which have the string "sda" or "sdb" in their device name.

for more usage document please visti the hd-idle site http://hd-idle.sourceforge.net/
