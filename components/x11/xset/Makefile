#
# This file and its contents are supplied under the terms of the
# Common Development and Distribution License ("CDDL"), version 1.0.
# You may only use this file in accordance with the terms of version
# 1.0 of the CDDL.
#
# A full copy of the text of the CDDL should have accompanied this
# source.  A copy of the CDDL is also available via the Internet at
# http://www.illumos.org/license/CDDL.
#

#
# Copyright 2015 Aurelien Larcher
#

include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=           xset
COMPONENT_VERSION=        1.2.3
COMPONENT_FMRI=           x11/xset
COMPONENT_CLASSIFICATION= System/X11
COMPONENT_SUMMARY=  the xset X server configuration utility
COMPONENT_SRC=      $(COMPONENT_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=  $(COMPONENT_SRC).tar.bz2
COMPONENT_ARCHIVE_HASH= \
  sha256:4382f4fb29b88647e13f3b4bc29263134270747fc159cfc5f7e3af23588c8063
COMPONENT_ARCHIVE_URL= \
  http://www.x.org/releases/individual/app/xset-1.2.3.tar.bz2
COMPONENT_PROJECT_URL = http://www.x.org/
COMPONENT_LICENSE=      MIT License
COMPONENT_LICENSE_FILE= xset.license

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

PATH=/usr/gnu/bin:/usr/bin

build: $(BUILD_32_and_64)

install: $(INSTALL_32_and_64)

test: $(NO_TESTS)


REQUIRED_PACKAGES += system/library
REQUIRED_PACKAGES += x11/library/libx11
REQUIRED_PACKAGES += x11/library/libxext
REQUIRED_PACKAGES += x11/library/libxmuu
REQUIRED_PACKAGES += x11/library/libxxf86misc
