.. SPDX-FileCopyrightText: Huawei Inc.
..
.. SPDX-License-Identifier: CC-BY-4.0

==========
.workspace
==========

The ``.workspace`` job assembles a *git-repo* workspace, as described by
*manifest* file. This job is a foundation for other jobs. 

This workspace is **not** constructed in ``$CI_PROJECT_DIR``, which is by
GitLab runner. To avoid clashes with any files that may be present there, it is
constructed in a temporary directory. Additional logic stores and restores the
path of that directory between the code in ``before_script``, ``script`` and
``after_script`` as those execute in separate shell processes.

Constraints
===========

This job uses the ``ostc-builder`` container image, mainly for convenience, as
it is often extended to perform other tasks, such as bitbake builds. Other
containers can be used, as long as they have the ``repo`` program
pre-installed.

In addition this job uses the ``large-disk`` tag to be scheduled on a machine
with access to a shared NFS volume with git mirrors, that greatly speed up the
process of constructing the workspace from scratch.

Variables
=========

OHOS_MANIFEST_URL
-----------------

The URL consumed by git-repo. You only want to change this if you forked the
entire OHOS infrastructure and want to use it in private.

The default value is ``https://git.ostc-eu.org/OSTC/OHOS/manifest``.

If you change the default value, please set ``OHOS_MANIFEST_MIRROR`` as well.

OHOS_MANIFEST_BRANCH
--------------------

The name of the git branch of the manifest repository. Unless special
circumstances apply this does not need to be customized.

For testing changes coming into the *manifest* repository itself, use
``$CI_COMMIT_REF_NAME``, which will check out the manifest as described by the
specific commit being tested. 

The default value is ``develop``.

OHOS_MANIFEST_NAME
------------------

The name of the manifest file from the repository mentioned above.

The default value is ``default.xml``.

OHOS_MANIFEST_MIRROR
--------------------

Name of the ``git-repo`` mirror matching to use, expressed as a directory name
in the shared disk volume. Check the section about git-repo mirror below, for
details.

The default value is ``ostd-develop``.

OHOS_CI_GIT_REPO_PATH
---------------------

The path of the git repository to deviate from what the git-repo manifest
describes. This variable should be used for constructing CI jobs for
repositories directly described by the manifest.

When set to a non-empty value, the specified git repository will be first
checked out by the git-repo according to what is described in the manifest, and
then changed again, to point to ``$CI_COMMIT_SHA``. The logic in the script
supports the forked repository workflow, adding any remotes as appropriate. 

The default value is the empty string.

Local git-repo Mirror
=====================

The ``.workspace`` job relies on a git-repo mirror that is mounted into the
execution environment provided by the GitLab worker. The mirror is created and
kept up-to-date by the scheduled run of the pipeline in `ostc-manifest-mirror
repository`_

.. _ostc-manifest-mirror repository: https://git.ostc-eu.org/OSTC/infrastructure/ostc-manifest-mirror

When the mirror is out-of-date additional git revisions needed to construct the
workspace are fetched form the respective upstream repositories. Some of the
git repositories described by the manifest are rather large and are hosted on
infrastructure outside of the OSTC cloud provider, making this an important
optimization.

The mirror is automatically published in `<https://cache.ostc-eu.org/git-repo-mirrors/>`_,
with two specific mirrors being available: *ostc-dev* and *gitee-dev*.
