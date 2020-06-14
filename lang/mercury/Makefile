# $OpenBSD$

COMMENT =		Mercury is a pure logic programming language

V =			20.01.2
DISTNAME =		mercury-srcdist-$V
PKGNAME =		mercury-$V
CATEGORIES =		lang

HOMEPAGE =		https://mercurylang.org

MAINTAINER =		Mathieu Kerjouan <niamkik@protonmail.com>

PERMIT_PACKAGE =	Yes

BUILD_DEPENDS =		devel/bison

FLAVORS=		minimal erlang
FLAVORS?= 

CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS =	--enable-sanitizers 
CONFIGURE_ENV =		CC=cc CPP=cpp
MAKE_ENV =		PARALLEL=-j2
USE_GMAKE =		Yes
YACC =			bison

EXTRACT_SUFX =		.tar.gz
WRKDIST =		${WRKDIR}/${DISTNAME}

MASTER_SITES =		http://dl.mercurylang.org/release/

CONFLICT_MARKER =	mercury-*-erlang mercury-*-minimal

do-test:
	cd ${WRKBUILD}/tests && mmake

.include <bsd.port.mk>

.if ${FLAVOR:Mminimal}
CONFIGURE_ARGS += 	--enable-minimal-install
CONFLICT_MARKER =	mercury-* mercury-*-minimal
.endif

.if ${FLAVOR:Merlang}
CONFIGURE_ARGS += 	--enable-erlang-grade
BUILD_DEPENDS +=	lang/erlang/21
CONFLICT_MARKER =	mercury-* mercury-*-minimal
.endif

