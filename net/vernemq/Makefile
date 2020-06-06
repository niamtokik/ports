# $OpenBSD$

COMMENT =		A distributed MQTT message broker based on Erlang/OTP

V =			1.10.2
DISTNAME =		$V
PKGNAME =		vernemq-$V
CATEGORIES =		net

HOMEPAGE =		https://vernemq.com/

MAINTAINER =		Mathieu Kerjouan <niamkik@protonmail.com>

PERMIT_PACKAGE =	Yes

BUILD_DEPENDS =		databases/leveldb lang/erlang/21 devel/gmake

USE_GMAKE =		Yes
CONFIGURE_STYLE =	none
EXTRACT_SUFX =		.tar.gz
WRKDIST =		${WRKDIR}/${PKGNAME}

MASTER_SITES =		https://github.com/vernemq/vernemq/archive/

.include <bsd.port.mk>
