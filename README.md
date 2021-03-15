<!--
SPDX-License-Identifier: Apache-2.0
SPDX-FileCopyrightText: Huawei Inc.
-->

meta-ohos manifest
==================

This repository contains **repo** tool manifests for working with **meta-ohos**. 

For more info on **meta-ohos** see: [https://git.ostc-eu.org/OSTC/OHOS/meta-ohos](https://git.ostc-eu.org/OSTC/OHOS/meta-ohos)

CI Process
==========

This repository contains a `.gitlab-ci.yml` file which is used by GitLab to
perform automatic builds. Please refer to it for a detailed description.

Some of the definitions in `.ostc-ci/*.yaml` are re-used by other repositories,
most notably the `meta-ohos` and `xts-acts` repositories, as those participate
most closely with development of the CI system. Making changes here may require
coordinated updates in those repositories as well.
