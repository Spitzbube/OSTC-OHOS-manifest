.. SPDX-FileCopyrightText: Huawei Inc.
..
.. SPDX-License-Identifier: CC-BY-4.0

Continuous Integration
======================

Shared Job Definitions
----------------------

The following GitLab job definitions are shared with other repositories. They
can be customized at the level of a particular git repository, but in general
constitute the set of supported build configurations.

linux-qemu-x86
..............

This job builds ``openharmony-image-base-tests`` using ``FLAVOUR=linux`` and
``MACHINE=qemux86``. This job checks that OpenHarmony software can be built for
a basic 32bit x86 virtual machine.

The cache for this job is publicly available.

linux-qemu-x86_64
.................

This job builds ``openharmony-image-base-tests`` using ``FLAVOUR=linux`` and
``MACHINE=qemux86-64``. This job checks that OpenHarmony software can be built
for a basic 64bit x86 virtual machine.

The cache for this job is publicly available.

linux-qemu-arm
..............

This job builds ``openharmony-image-base-tests`` using ``FLAVOUR=linux`` and
``MACHINE=qemuarm``. This job checks that OpenHarmony software can be built for
a basic 32bit ARMv7 virtual machine.

The cache for this job is publicly available.

linux-qemu-arm64
................

This job builds ``openharmony-image-base-tests`` using ``FLAVOUR=linux`` and
``MACHINE=qemuarm64``. This job checks that OpenHarmony software can be built
for a basic 64bit ARMv8 virtual machine.

The cache for this job is publicly available.

linux-seco-intel-b68
....................

This job builds ``openharmony-image-base-tests`` using ``FLAVOUR=linux`` and
``MACHINE=seco-intel-b68``. This job checks that OpenHarmony software can be
built for the SECO B68 development board, which contains an Intel x86_64 SoC.

The cache for this job is not public, pending legal review of any firmware that
may be included.

linux-seco-imx8mm-c61
.....................

This job builds ``openharmony-image-base-tests`` using ``FLAVOUR=linux`` and
``MACHINE=seco-imx8mm-c61``. This job checks that OpenHarmony software can be
built for the SECO C61 development board, which contains an iMX8 SoC.

The cache for this job is not public, as it contains proprietary elements that
cannot be redistributed without an agreement with Freescale.

linux-stm32mp1-av96
...................

This job builds ``openharmony-image-base-tests`` using ``FLAVOUR=linux`` and
``MACHINE=stm32mp1-av96``. This job checks that OpenHarmony software can be
built for the 96Boards Avenger development board, which contains an STM32MP157
SoC.

The cache for this job is not public, pending legal review of any firmware that
may be included.

zephyr-qemu-x86
...............

This job builds ``zephyr-philosophers`` using ``FLAVOUR=zephyr`` and
``MACHINE=qemu-x86``. This job checks that Zephyr can be built for a basic 32bit
x86 virtual machine.

The cache for this job is publicly available.

zephyr-qemu-cortex-m3
.....................

This job builds ``zephyr-philosophers`` using ``FLAVOUR=zephyr`` and
``MACHINE=qemu-cortex-m3``. This job checks that Zephyr can be built for a basic
32bit ARM micro-controller virtual machine.

The cache for this job is publicly available.

zephyr-96b-nitrogen
...................

This job builds ``zephyr-philosophers`` using ``FLAVOUR=zephyr`` and
``MACHINE=96b-nitrogen``. This job checks that Zephyr can be built for the
96Boards Nitrogen development board, which contains an nRF52832 SoC.

The cache for this job is not public, pending legal review of any firmware that
may be included.

zephyr-96b-avenger
..................

This job builds ``zephyr-philosophers`` using ``FLAVOUR=zephyr`` and
``MACHINE=96b-avenger96``. This job checks that Zephyr can be built for the
96Boards Avenger development board cortex-M3 core, embedded into STM32MP157 SoC.

The cache for this job is not public, pending legal review of any firmware that
may be included.

freertos-armv5
..............

This job builds ``freertos-demo`` using ``FLAVOUR=freertos`` and
``MACHINE=qemuarmv5``. This job checks that FreeRTOS can be built for a basic
32bit ARMv5 micro-controller virtual machine.

The cache for this job is publicly available.

Special Jobs
------------

linux-glibc-qemu-x86_64
.......................

This job extends ``linux-qemu-x86_64`` and differs in the following way.

This job performs a build with the libc switched to ``glibc``. It only runs on a
schedule that is defined in the GitLab project settings for the `manifest`
repository. In practice it runs daily to check if the Linux favour could be
switched back to ``glibc``, from the default ``musl`` that is used right now.

Implementation Highlights
-------------------------

Implementation details are stored directly in the manifest repository, as code
comments. Only specific highlights are listed below.

Local git-repo Mirror
.....................

The ``.workspace`` job relies on a git-repo mirror that is mounted into the
execution environment provided by the GitLab worker. The mirror is created and
kept up-to-date by the scheduled run of the pipeline in `ostc-manifest-mirror
repository`_

.. _ostc-manifest-mirror repository: https://git.ostc-eu.org/OSTC/infrastructure/ostc-manifest-mirror

When the mirror is out-of-date additional git revisions needed to construct the
workspace are fetched form the respective upstream repositories. Some of the git
repositories described by the manifest are rather large and are hosted on
infrastructure outside of the OSTC cloud provider, making this an important
optimization.

The mirror is automatically published in https://cache.ostc-eu.org/git-repo-mirrors/ostc-develop

Bitbake downloads and sstate-cache
..................................

The ``.workspace`` job configures bitbake to use a persistent directory that is
shared between CI jobs, for the location of the ``download`` directory as well
as the ``sstate-cache`` directory.

The job is using GitLab runner tags to schedule jobs in the environment where
that shared storage is available. When a new dependency is added or when the
layers and recipes are changed or updated, the download is automatically
populated with the necessary source archives. Similarly ``sstate-cache`` is
populated by all the build jobs present throughout the CI system.

Due to legal restrictions, the caches are split into two pairs, public and private.
The public cache is automatically published in https://cache.ostc-eu.org/bitbake/
The private cache, which is used by default, is available on the same volume but it is
not shared anywhere.

In case the cache is fed with a software package that is, in retrospective
somehow problematic, for example, by not being freely redistributable, the cache
can be purged at will.

For details on how cache selection and bitbake configuration looks like, please
refer to the pipeline source code.
