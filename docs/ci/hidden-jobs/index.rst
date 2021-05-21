.. SPDX-FileCopyrightText: Huawei Inc.
..
.. SPDX-License-Identifier: CC-BY-4.0

Hidden Jobs
===========

There's a number of *hidden jobs*, which start with the dot character, that are
used as foundation for the set of :doc:`shared jobs <../shared-jobs>`. Hidden
jobs do not participate in any pipeline directly. They can only be used as
templates, using the ``extends: ...`` mechanism, to share and reuse
implementation details.

.. toctree::
   :maxdepth: 1
      
   workspace
   bitbake-workspace
   build-linux
   build-zephyr
   build-freertos
   build-recipe
   build-image
   build-docs
   lava-test
   lava-report
   aggregate-docs
