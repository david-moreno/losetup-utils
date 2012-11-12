losetup-utils
=============

Utilities to create, mount and unmount encrypted volumes using losetup

losetup is still fast, easy and practical in many situations like:

* Sending sensible information over the internet.
* Transporting sensible information on CDs, DVDs, pendrives, etc.
* Storing private data on a hard disk.
* Storing private data on the cloud.

This scripts attempts to use losetup a bit easier and faster.

Install
-------

You can clone this repository or download it as a zip file. To clone:

    $ git clone https://github.com/david-moreno/losetup-utils

Move to the losetup-utils directory:

    $ cd losetup-utils

Copy the scripts to `/usr/bin` (or another directory with executables in your *$PATH*):

    # cp *loopfs* /usr/bin      # You must be root.

Alternatively, you can use *sudo*:

    $ sudo cp *loopfs* /usr/bin

Usage
-----

Creates a 500 MB encrypted volume (will ask for a password):

    # mkloopfs myvolume 500
      ...
      password:
      ...
      ext2 volume 'myvolume' created successfully

Mounts the volume in `/mnt/volume`.
Will ask for a password and finally, informs us which loop device is using (*loop0* in this case):

    # mount.loopfs myvolume /mnt/volume
      password:
      'myvolume' mounted in '/mnt/volume/' using '/dev/loop0' loop device

Unmounts the volume using *loop0*:

    # umount.loopfs /dev/loop0
      /dev/loop0 unmounted

Examples
--------

If you want to create a volume specifying units different than megabytes:

    # mkloopfs myvolume 2 G      # Creates a 2GB volume.
    # mkloopfs myvolume 1 Y      # 1YB volume.

You can specify a cipher, a filesystem type and a label for your volume.
To create a 4GB volume with an *ext4* filesystem using the *serpent* cipher and labeled "my secret volume" you must write:

    # mkloopfs secret_volume 4 G serpent ext4 "my secret volume"

If you specified a cipher for a volume, you must indicate it when mounting:

    # mount.loopfs secret_volume /mnt/volume serpent

All the volumes unmounts in the same way, regardless of the filesystem or encryption ( *loop0* in this case):

    # umount.loopfs /dev/loop0