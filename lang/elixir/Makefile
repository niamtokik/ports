# $OpenBSD: Makefile,v 1.60 2021/03/28 13:45:31 jasper Exp $

COMMENT=		functional language for building scalable applications

V=			1.11.4
EPOCH=			2
GH_ACCOUNT=		elixir-lang
GH_PROJECT=		elixir
GH_TAGNAME=		v$V
DISTNAME=		${GH_PROJECT}-$V
CATEGORIES=		lang

HOMEPAGE=		https://elixir-lang.org/

MAINTAINER=		Jasper Lievisse Adriaanse <jasper@openbsd.org>

# Apache2
PERMIT_PACKAGE=	Yes

MODULES=		lang/erlang

ALL_TARGET=		# empty

TEST_TARGET=		test
PORTHOME=		${WRKDIR}

MAKE_FLAGS=		PREFIX="${PREFIX}" \
			MAN_PREFIX="${PREFIX}/man" \
			Q=""

pre-configure:
	${SUBST_CMD} ${WRKSRC}/bin/elixir \
		${WRKSRC}/Makefile \
		${WRKSRC}/lib/elixir/generate_app.escript

pre-install:
	-rm ${WRKSRC}/bin/*.{beforesubst,orig}

.include <bsd.port.mk>
