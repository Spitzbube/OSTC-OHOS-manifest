.. SPDX-FileCopyrightText: Huawei Inc.
..
.. SPDX-License-Identifier: CC-BY-4.0

The manifest Repository
=======================

.. _manifest repository: https://git.ostc-eu.org/OSTC/OHOS/manifest.git

The `manifest repository`_ contains the "map" to all the other repositories used
by OpenHarmony and is thus important from CI point of view.

The *manifest* repository also contains job definitions that pipelines defined
in other repositories can include. Those are all stored in the `.ostc-ci`
directory. Internally, in the manifest repository, the same rules are used to
create a git-repo workspace, synchronize all the git repositories, initialize
and configure BitBake and build BitBake recipes corresponding to supported
reference boards.

.. toctree::
   :maxdepth: 1

   ci/index
