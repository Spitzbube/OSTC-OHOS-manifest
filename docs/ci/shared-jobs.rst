.. SPDX-FileCopyrightText: Huawei Inc.
..
.. SPDX-License-Identifier: CC-BY-4.0

Shared Job Definitions
----------------------

The following GitLab job definitions are shared with other repositories. They
can be customized at the level of a particular git repository, but in general
constitute the set of supported build configurations.

linux-qemu-x86
..............

This job extends :doc:`hidden-jobs/build-linux` and builds
``openharmony-image-base-tests`` and ``openharmony-image-extra-tests`` using
the Linux flavour of All Scenarios OS and ``MACHINE=qemux86``. This job checks that
All Scenarios OS software can be built for a basic 32bit x86 virtual machine.

The cache for this job is publicly available.

linux-qemu-x86_64
.................

This job extends :doc:`hidden-jobs/build-linux` and builds
``openharmony-image-base-tests`` and ``openharmony-image-extra-tests`` using
the Linux flavour of All Scenarios OS and ``MACHINE=qemux86-64``. This job checks that
All Scenarios OS software can be built for a basic 64bit x86 virtual machine.

The cache for this job is publicly available.

linux-qemu-arm
..............

This job extends :doc:`hidden-jobs/build-linux` and builds
``openharmony-image-base-tests`` and ``openharmony-image-extra-tests`` using
the Linux flavour of All Scenarios OS and ``MACHINE=qemuarm``. This job checks that
All Scenarios OS software can be built for a basic 32bit ARMv7 virtual machine.

The cache for this job is publicly available.

linux-qemu-arm64
................

This job extends :doc:`hidden-jobs/build-linux` and builds
``openharmony-image-base-tests`` and ``openharmony-image-extra-tests`` using
the Linux flavour of All Scenarios OS and ``MACHINE=qemuarm64``. This job checks that
All Scenarios OS software can be built for a basic 64bit ARMv8 virtual machine.

The cache for this job is publicly available.

linux-seco-intel-b68
....................

This job extends :doc:`hidden-jobs/build-linux` and builds
``openharmony-image-base-tests`` and ``openharmony-image-extra-tests`` using
the Linux flavour of All Scenarios OS and ``MACHINE=seco-intel-b68``. This job
checks that All Scenarios OS software can be built for the SECO B68 development
board, which contains an Intel x86_64 SoC.

The cache for this job is not public, pending legal review of any firmware that
may be included.

linux-seco-imx8mm-c61
.....................

This job extends :doc:`hidden-jobs/build-linux` and builds
``openharmony-image-base-tests`` and ``openharmony-image-extra-tests`` using
the Linux flavour of All Scenarios OS and ``MACHINE=seco-imx8mm-c61``. This job
checks that All Scenarios OS software can be built for the SECO C61 development
board, which contains the NXP i.MX 8M Mini SoC, which implements 64bit ARMv8
architecture.

The cache for this job is not public, as it contains proprietary elements that
cannot be redistributed without an agreement with Freescale.

linux-stm32mp1-av96
...................

This job extends :doc:`hidden-jobs/build-linux` and builds
``openharmony-image-base-tests`` and ``openharmony-image-extra-tests`` using
the Linux flavour of All Scenarios OS and ``MACHINE=stm32mp1-av96``. This job checks
that All Scenarios OS software can be built for the 96Boards Avenger development
board, which contains the STM32MP157 SoC, which implements 32bit ARMv7
architecture.

The cache for this job is not public, pending legal review of any firmware that
may be included.

zephyr-qemu-x86
...............

This job extends :doc:`hidden-jobs/build-zephyr` and builds
``zephyr-philosophers`` using the Zephyr flavour of All Scenarios OS and
``MACHINE=qemu-x86``. This job checks that Zephyr can be built for a basic
32bit x86 virtual machine.

The cache for this job is publicly available.

zephyr-qemu-cortex-m3
.....................

This job extends :doc:`hidden-jobs/build-zephyr` and builds
``zephyr-philosophers`` using the Zephyr flavour of All Scenarios OS and
``MACHINE=qemu-cortex-m3``. This job checks that Zephyr can be built for a
basic 32bit ARM micro-controller virtual machine.

The cache for this job is publicly available.

zephyr-96b-nitrogen
...................

This job extends :doc:`hidden-jobs/build-zephyr` and builds
``zephyr-philosophers`` using the Zephyr flavour of All Scenarios OS and
``MACHINE=96b-nitrogen``. This job checks that Zephyr can be built for the
96Boards Nitrogen development board, which contains an nRF52832 SoC.

The cache for this job is not public, pending legal review of any firmware that
may be included.

zephyr-96b-avenger
..................

This job extends :doc:`hidden-jobs/build-zephyr` and builds
``zephyr-philosophers`` using the Zephyr flavour of All Scenarios OS and
``MACHINE=96b-avenger96``. This job checks that Zephyr can be built for the
96Boards Avenger development board cortex-M3 core, embedded into STM32MP157
SoC.

The cache for this job is not public, pending legal review of any firmware that
may be included.

freertos-armv5
..............

This job extends :doc:`hidden-jobs/build-freertos` and builds ``freertos-demo``
using the FreeRTOS flavour of All Scenarios OS and ``MACHINE=qemuarmv5``. This job
checks that FreeRTOS can be built for a basic 32bit ARMv5 micro-controller
virtual machine.

The cache for this job is publicly available.
