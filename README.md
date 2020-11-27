meta-ohos
==========

This repository contains **repo** tool manifests for working with **meta-ohos**. 
**meta-ohos** is a bitbake layer for building openharmony images using the bitbake infrastructure.

## Getting started

To start working with **meta-ohos** first install git repo:

    $ sudo add-apt-repository ppa:zyga/oh-tools
    $ sudo apt-get update
    $ sudo apt-get install git-repo

Once git repo has been installed we can use it to clone the necessary repositories:

    $ mkdir meta-ohos; cd meta-ohos
    $ repo init -u https://git.ostc-eu.org/incubate/yocto-ohos.git
    $ repo sync
    $ cd poky
    poky$ . oe-init-build-env

Working directory will automatically change to ./build. Add layers for Zephyr.
Layers for poky were added automatically by sourcing `oe-init-build-env`.

    build$ bitbake-layers add-layer ../meta-openembedded/meta-oe
    build$ bitbake-layers add-layer ../meta-openembedded/meta-python
    build$ bitbake-layers add-layer ../meta-zephyr

Build distro of your choice:

    build$ DISTRO=poky-tiny MACHINE=qemux86 bitbake core-image-minimal
    build$ DISTRO=zephyr MACHINE=qemu-x86 bitbake zephyr-philosophers

For Zephyr, `zephyr-philosophers` is the one of sample applications available
in meta-zephyr layer by Yocto project. It's easy to build other samples using
recipes available in `meta-zephyr/recipes-kernel/zephyr-kernel/` directory.

When the build is finished, you can run the image by issuing:

    # For poky
    build$ runqemu qemux86 ramfs qemuparams="-nographic"
    # For Zephyr
    build$ DEPLOY_DIR_IMAGE=tmp-newlib/deploy/images/qemu-x86 runqemu qemu-x86

After successful bootup, you should see following:

    # For Zephyr
    Booting from ROM..*** Booting Zephyr OS build zephyr-v2.4.0  ***
    Philosopher 0 [P: 3]  THINKING [  300 ms ]
    Philosopher 1 [P: 2]   EATING  [  575 ms ]
    Philosopher 2 [P: 1]        STARVING
    Philosopher 3 [P: 0]   EATING  [  525 ms ]
    Philosopher 4 [C: -1]  THINKING [  475 ms ]

    # For poky
    qemux86 login:
    # Default login is _root_ without a password.
    # After login you should see prompt:
    root@qemux86:~#

To exit qemu, you can either shut down the system:

    root@qemux86:~# poweroff -f

or close qemu using key combination:

    Ctrl-a followed by 'x'

