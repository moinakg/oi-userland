#
# CDDL HEADER START
#
# The contents of this file are subject to the terms of the
# Common Development and Distribution License (the "License").
# You may not use this file except in compliance with the License.
#
# You can obtain a copy of the license at usr/src/OPENSOLARIS.LICENSE
# or http://www.opensolaris.org/os/licensing.
# See the License for the specific language governing permissions
# and limitations under the License.
#
# When distributing Covered Code, include this CDDL HEADER in each
# file and include the License file at usr/src/OPENSOLARIS.LICENSE.
# If applicable, add the following below this CDDL HEADER, with the
# fields enclosed by brackets "[]" replaced with your own identifying
# information: Portions Copyright [yyyy] [name of copyright owner]
#
# CDDL HEADER END
#
# Copyright (c) 2011, 2012, Oracle and/or its affiliates. All rights reserved.
#
include ../../../make-rules/shared-macros.mk

COMPONENT_NAME=		isc-dhcp
COMPONENT_VERSION=	4.3.4
IPS_COMPONENT_VERSION=	4.3.4
COMPONENT_SRC_NAME=	dhcp
COMPONENT_SRC=		$(COMPONENT_SRC_NAME)-$(COMPONENT_VERSION)
COMPONENT_ARCHIVE=	$(COMPONENT_SRC).tar.gz
COMPONENT_PROJECT_URL=	http://www.isc.org/software/dhcp/
COMPONENT_ARCHIVE_URL=  \
    http://ftp.isc.org/isc/dhcp/$(COMPONENT_VERSION)/$(COMPONENT_ARCHIVE)
COMPONENT_ARCHIVE_HASH= \
    sha256:f5115aee3dd3e6925de4ba47b80ab732ba48b481c8364b6ebade2d43698d607e
COMPONENT_BUGDB=	service/dhcp-server

include $(WS_TOP)/make-rules/prep.mk
include $(WS_TOP)/make-rules/configure.mk
include $(WS_TOP)/make-rules/ips.mk

# Parallel build fails
COMPONENT_BUILD_ARGS =

CONFIGURE_SCRIPT	= $(@D)/configure
COMPONENT_PRE_CONFIGURE_ACTION+=	$(CP) -R $(SOURCE_DIR)/* $(@D)/

CONFIGURE_OPTIONS  +=	--sysconfdir=$(ETCDIR)/inet
CONFIGURE_OPTIONS  +=	--sbindir=$(USRLIBDIR)/inet
CONFIGURE_OPTIONS  +=	--bindir=$(USRSBINDIR)
CONFIGURE_OPTIONS  +=	--enable-use-sockets
CONFIGURE_OPTIONS  +=	--enable-ipv4-pktinfo


# Disable message in omapip/errwarn.c.
CPPFLAGS  +=	        -DNOMINUM
CONFIGURE_OPTIONS  +=   CPPFLAGS="$(CPPFLAGS)"

COMPONENT_TEST_DIR =	$(@D)

build:		$(BUILD_32)

install:	build $(INSTALL_32) $(PROTO_DIR)/dhcpd.leases

test:	$(TEST_32)

$(PROTO_DIR)/dhcpd.leases:	$(INSTALL_32)
	$(TOUCH) $@

REQUIRED_PACKAGES += SUNWcs
REQUIRED_PACKAGES += system/library
