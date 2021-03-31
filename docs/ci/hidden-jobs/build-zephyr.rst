.. SPDX-FileCopyrightText: Huawei Inc.
..
.. SPDX-License-Identifier: CC-BY-4.0

=============
.build-zephyr
=============

The ``.build-zephyr`` job extends the :doc:`bitbake-workspace` job. It sets
``OHOS_BUILD_FLAVOUR`` to ``zephyr`` and builds the ``zephyr-philosophers``
test image.

Usage Guide
===========

This job is not intended for direct use. Instead it serves as a base for all
the Zephyr-specific :doc:`../shared-jobs`.
