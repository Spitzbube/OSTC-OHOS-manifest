# SPDX-FileCopyrightText: Huawei Inc.
#
# SPDX-License-Identifier: Apache-2.0

.PHONY: all
all:
	sphinx-build -W -C \
		-D html_theme=sphinx_rtd_theme \
		-D project='All Scenario OS Manifest Repository' \
		-D copyright='Huawei Inc' \
		. build

clean:
	rm -rf ./build
