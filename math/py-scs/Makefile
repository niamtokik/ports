# $OpenBSD: Makefile,v 1.6 2021/01/04 14:06:35 sthen Exp $

COMMENT =		Python interface to SCS

MODPY_EGG_VERSION =	2.1.1-2
DISTNAME =		scs-${MODPY_EGG_VERSION}
V =			${MODPY_EGG_VERSION:S/-/./}
PKGNAME =		py-scs-${V}
CATEGORIES =		math
REVISION =		3

MAINTAINER =		Paul Irofti <paul@irofti.net>

# MIT
PERMIT_PACKAGE =	Yes

MODULES =		lang/python

BUILD_DEPENDS =		${RUN_DEPENDS}
RUN_DEPENDS =		math/py-numpy${MODPY_FLAVOR} \
			math/py-scipy${MODPY_FLAVOR}

MODPY_PI =		Yes
MODPY_SETUPTOOLS =	Yes
MODPY_PYTEST =		Yes

FLAVORS =		python3
FLAVOR =		python3

TEST_DEPENDS =		${FULLPKGNAME}:${BUILD_PKGPATH}

.include <bsd.port.mk>
