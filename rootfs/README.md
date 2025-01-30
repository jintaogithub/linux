# Overview

This folder maintains a few handy rootfs for different ARCH and setup, just to
allow me to create a working Linux build asap.

1. The folder name should be self-reflecting
1. To create a initramfs.img

   ```bash
   find . | cpio -o -H newc | gzip > ../initramfs.img
   ```

# One-liners

*Assuming you are in the root path of kernel repo*

1. x86_64_initramfs_busybox

   ```bash
   cd rootfs/x86_64_initramfs_busybox
   find . | cpio -o -H newc | gzip > ../../initramfs.img
   cd ../..
   qemu-system-x86_64 \
    -kernel arch/x86/boot/bzImage \
    -initrd initramfs.img \
    -append "console=ttyS0 rdinit=/init" \
    -nographic
   ```