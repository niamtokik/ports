# $OpenBSD: Makefile,v 1.18 2021/02/15 21:30:16 sthen Exp $

COMMENT =	parsing library for RIPE Atlas measurement results

MODPY_EGG_VERSION =	1.3.0
DISTNAME =	ripe.atlas.sagan-${MODPY_EGG_VERSION}
PKGNAME =	py-${DISTNAME}
REVISION =	4

CATEGORIES =	net

HOMEPAGE =	https://github.com/RIPE-NCC/ripe.atlas.sagan

# GPLv3
PERMIT_PACKAGE =	Yes

MODPY_PI =		Yes
MODPY_SETUPTOOLS =	Yes
MODPY_PYTEST =		Yes
MODPY_PYTEST_ARGS =	tests/*.py

MODULES =	lang/python

FLAVORS =	python3
FLAVOR =	python3

RUN_DEPENDS =	devel/py-dateutil${MODPY_FLAVOR} \
		devel/py-tz${MODPY_FLAVOR} \
		security/py-openssl${MODPY_FLAVOR}

TEST_DEPENDS =	devel/py-nose${MODPY_FLAVOR}

.include <bsd.port.mk>
