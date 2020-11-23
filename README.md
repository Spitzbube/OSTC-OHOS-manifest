meta-ohos
==========

This repository contains **repo** tool manifests for working with **meta-ohos**. 
**meta-ohos** is a bitbake layer for building openharmony images using the bitbake infrastructure.

## Getting started

To start working with **meta-ohos** issue following commands:

    $ repo init -u https://git.ostc-eu.org/incubate/yocto-ohos.git
    $ repo sync
    $ cd poky
    poky$ . oe-init-build-env
    # Working directory will automatically change to poky/build
    poky/build$ DISTRO=poky-tiny MACHINE=qemux86 bitbake core-image-minimal

When the build is finished, you can run the image by issuing:

    poky/build$ runqemu qemux86 ramfs qemuparams="-nographic"

After successful bootup, you should see following prompt:

    qemux86 login:

Default login is _root_ without a password. After logging you should see prompt:

    root@qemux86:~#

To exit qemu, you can either shut down the system:

    root@qemux86:~# poweroff -f

or close qemu using key combination:

    Ctrl-a followed by 'x'

