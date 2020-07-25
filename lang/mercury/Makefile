# $OpenBSD$

COMMENT-main =		Mercury is a pure logic programming language
COMMENT-minimal =	Mercury is a pure logic programming language

CATEGORIES =		lang
V =			20.06
DISTNAME =		mercury-srcdist-$V
PKGNAME =		mercury-$V
PKGNAME-main =		mercury-$V
PKGNAME-minimal =	mercury-$V-minimal

REVISION-main =		0
REVISION-minimal =	0

MULTI_PACKAGES =	-main -minimal

BUILD_DEPENDS =		devel/bison ${MODGNU_AUTOCONF_DEPENDS}

HOMEPAGE =		https://mercurylang.org

MAINTAINER =		Mathieu Kerjouan <niamkik@protonmail.com>

PERMIT_PACKAGE =	Yes

CONFIGURE_STYLE =	gnu
CONFIGURE_ARGS =       --enable-sanitizers --enable-erlang-grade --disable-csharp-grade
CONFIGURE_ARGS +=      --enable-hlc-prof-grades --enable-hlc-low-level-debug-grades
CONFIGURE_ENV =		CC=cc CPP=cpp
MAKE_ENV =		PARALLEL=-j2
USE_GMAKE =		Yes
YACC =			bison
AUTOCONF_VERSION = 	2.69

EXTRACT_SUFX =		.tar.gz
WRKDIST =		${WRKDIR}/${DISTNAME}

MASTER_SITES =		http://dl.mercurylang.org/release/

CONFLICT_MARKER =	mercury-*-minimal

SUBST_VARS =		V

do-test:
	cd ${WRKBUILD}/tests && mmake

.include <bsd.port.mk>
