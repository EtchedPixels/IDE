# IDE
A simple IDE emulator library along with some simple tools and patches to use
it.

# ide.c and ide.h

Simple emulation for an IDE device. It keeps the identify data for the disk and
lots of free space for future features in the first 1K, and then the rest is
data. Simple as that

# makedisk.c

Tool for creating disk images

#ide-patch-coco-xroar

Patch to xroar-0.33.2 to add basic support for IDE cartridges. Use with
-default-machine coco -cart ide -cart-rom hdblba13.rom

The interface emulates a Cloud 9 IDE controller with a DS1315 timer at 0xFF78/9
and with IDE at 0xFF50-8 (with the latched data at 0xFF58). The becker port
is at 0xFF40.

You need an hdbdos ROM that is set for the right addresses and built for the
right machine (COCO or Dragon). If you are using a small disk image you will
also need to set the HDBDOS base offset to a lower value. This is the offset
of the disk used for the COCO/Dragon floppy disk images so that the initial
area is clear for OS/9 (or Fuzix... 8-) )

See the hdbdos manual for more information on this:

http://www.frontiernet.net/~mmarlette/Cloud-9/Support/HDB-DOS%20User%20Manual.pdf

The path is currently hardcoded for one disk as hd0.img

makedisk 1 hd0.img

Start xroar and you should be in Disk BASIC. Now you can

DKSINI 0

type in code

SAVE "code"

DIR

and all should be good.

