# $OpenBSD: Makefile,v 1.61 2021/06/05 12:34:05 jasper Exp $

COMMENT=		functional language for building scalable applications

V=			1.12.1
GH_ACCOUNT=		elixir-lang
GH_PROJECT=		elixir
GH_TAGNAME=		v$V
DISTNAME=		${GH_PROJECT}-$V
CATEGORIES=		lang
REVISION =		0

HOMEPAGE=		https://elixir-lang.org/

# Apache2
PERMIT_PACKAGE=	Yes

# BUILD_DEPENDS+=		lang/erlang/23
MODULES=		lang/erlang
MODERL_VERSION=		23

ALL_TARGET=		# empty

TEST_TARGET=		test
PORTHOME=		${WRKDIR}

MAKE_FLAGS=		PREFIX="${PREFIX}" \
			MAN_PREFIX="${PREFIX}/man" \
			MODERL_VERSION="${MODERL_VERSION}" \
			Q=""

pre-configure:
	${SUBST_CMD} ${WRKSRC}/bin/elixir \
		${WRKSRC}/Makefile \
		${WRKSRC}/lib/elixir/generate_app.escript

pre-install:
	-rm ${WRKSRC}/bin/*.{beforesubst,orig}

.include <bsd.port.mk>
