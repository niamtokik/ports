# $OpenBSD: Makefile,v 1.14 2021/03/22 17:35:26 sthen Exp $

# IMPORTANT!  If you make any changes to the Python ports, be sure
# to also update files/CHANGES.OpenBSD for your change.  This is a
# requirement of the PSF license, if it constitutes a change to
# Python itself.

VERSION =		3.8
PATCHLEVEL =		.8
SHARED_LIBS =		python3.8 0.0
VERSION_SPEC =		>=3.8,<3.9
REVISION-main =		0

CONFIGURE_ARGS +=	--with-ensurepip=no
CONFIGURE_ARGS +=	--enable-loadable-sqlite-extensions

CONFIGURE_STYLE = autoconf

PORTROACH =             limit:^3\.8

TEST_IS_INTERACTIVE =	Yes

.include <bsd.port.mk>
