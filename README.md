losetup-utils
=============

Utilities to create, mount and unmount encrypted volumes using losetup

Usage
-----

Creates a 500 MB encrypted volume (will ask for a password):

    # mkloopfs myvolume 500
      ...
      password:
      ...
      ext2 volume 'myvolume' created successfully

Mounts the volume in `/mnt/volume`.
Will ask for a password and finally, will inform us about which loop device is using (loop0 in this case):

    # mount.loopfs myvolume /mnt/volume
      password:
      'myvolume' mounted in '/mnt/volume/' using '/dev/loop0' loop device

Unmounts the volume using loop0:

    # umount.loopfs /dev/loop0
      /dev/loop0 unmounted