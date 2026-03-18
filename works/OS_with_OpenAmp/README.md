# EMMC版的带有openamp的飞腾派OS
1.首先任意系统烧录到u盘作为引导系统

2.其次将三个文件拷贝到u盘的系统中并解压

3.解压后将u盘重新插入板上启动，在boot系统中使用以下指令
```
=>usb start (注意检查系统有没有检测到U盘存储设备，如果没有，请再执行usb stop、usb start)  
=>setenv bootargs console=ttyAMA1,115200 audit=0 earlycon=pl011,0x2800d000 root=/dev/sda1 rootwait rw;  
=>ext4load usb 0:1 0x90100000 /boot/Image  
=>ext4load usb 0:1 0x90000000 /boot/phytiumpi_firefly.dtb  
=>booti 0x90100000 - 0x90000000;  
```

>参考：https://gitee.com/phytium_embedded/phytium-pi-os/wikis/emmc%E9%A3%9E%E8%85%BE%E6%B4%BE%E7%B3%BB%E7%BB%9F%E7%BC%96%E8%AF%91%E4%B8%8E%E7%83%A7%E5%BD%95