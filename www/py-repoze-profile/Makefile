# $OpenBSD: Makefile,v 1.16 2021/02/27 22:27:15 daniel Exp $

COMMENT =	aggregate profiling for wsgi requests

MODPY_EGG_VERSION = 1.4
DISTNAME =	repoze.profile-${MODPY_EGG_VERSION}
PKGNAME =	py-${DISTNAME:S/./-/}
REVISION =	3

CATEGORIES =	www devel

# BSD-derived
PERMIT_PACKAGE =	Yes

RUN_DEPENDS =	devel/py-pyprof2calltree${MODPY_FLAVOR}

MODULES =	lang/python

FLAVORS =	python3
FLAVOR ?=

MODPY_PI =		Yes
MODPY_SETUPTOOLS =	Yes

post-install:
	${INSTALL_DATA_DIR} ${PREFIX}/share/doc/${MODPY_PY_PREFIX}repoze-profile
	${INSTALL_DATA} ${WRKSRC}/README.txt \
	    ${PREFIX}/share/doc/${MODPY_PY_PREFIX}repoze-profile

.include <bsd.port.mk>
