copperfrog-burnin-os
====================

Server Burnin OS Configuration

This configuration has been tested with CentOS 6.3.


Prerequisites
=============

The Following prerequisites need to be met in order for the build to succeed:

Packages needed:
- Group "Development Tools"
- texinfo
- scp
- wget
- asciidoc
- ncurses
- ncurses-devel
- hg
- gtk2-devel (for gconfig)
- glib2-devel (for gconfig)
- libglade2-devel (for gconfig)

See also: http://buildroot.org/downloads/manual/manual.html


Build
=====

    > cd buildroot-2012.11
    > make cf_burnin_defconfig


Output
======

In the output/images directory you will find the following files:

- rootfs.cpio.lzma -> Compresses initrd style root file system
- bzImage          -> Kernel image


How to boot
===========

Create a PXE boot setup with TFTP.
Copy rootfs.cpio.lzma and bzImage into the TFTP directory, e.g. /tftpboot/tools/cf and refer to the files in the menu configuration via

    LABEL CF_Burnin
      MENU LABEL ^4) Run CF Burnin software
      KERNEL tools/cf/bzImage
      APPEND initrd=tools/cf/rootfs.cpio.lzma vga=1


