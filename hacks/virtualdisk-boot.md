# Hacks: Virtualdisk Boot
-------------------------
It is possible to boot a virtual disk, a disk created mainly to be used by a
hypervisor; by the system bootloader, provided the disk is in format raw.

It has only been tested with GNU/Linux Debian Based distros as the virtual disk
main system, and using GRUB as the bootloader.

## How does it work
An operational system is just a bunch of files 
