# ICS OS Lib

<a href="bzImage" download>Download Kernel</a><br>
<a href="rootfs.cpio.gz" download>Download File system</a>

<p><b>Note:</b> The download will not occur in Edge version 12, IE, Safari 10 (and earlier), or Opera version 12 (and earlier).</p>

## Making the OS

1. cd fsystem
2. <code>find . | cpio -H newc -o | gzip -9 > ../rootfs.cpio.gz</code>
3. cd ..
4. qemu-system-i386 -kernel bzImage -initrd rootfs.cpio.gz

## Making an ISO

1. mkdir -p test/boot/grub
2. nano test/boot/grub/grub.cfg
3. 
menuentry "mySimpleOS" {
    linux /boot/bzImage
    initrd /boot/rootfs.cpio.gz
}

4. cp bzImage test/boot/
5. cp rootfs.cpio.gz test/boot/
6. grub-mkrescue -o mySimpleOS.iso test