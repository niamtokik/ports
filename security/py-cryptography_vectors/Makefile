# $OpenBSD: Makefile,v 1.30 2021/02/14 17:42:51 sthen Exp $

COMMENT=	test vectors for py-cryptography

MODPY_EGG_VERSION=	3.3.2
DISTNAME=	cryptography_vectors-${MODPY_EGG_VERSION}
PKGNAME=	${MODPY_PY_PREFIX}${DISTNAME}
CATEGORIES=	security

HOMEPAGE=	https://cryptography.io/

# dual: BSD or Apache 2
PERMIT_PACKAGE=	Yes

MODULES=	lang/python
MODPY_SETUPTOOLS= Yes
MODPY_PI=	Yes
MODPY_PI_DIR=	c/cryptography-vectors

FLAVORS=	python3
FLAVOR?=

.include <bsd.port.mk>
