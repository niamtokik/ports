# $OpenBSD: Makefile,v 1.38 2021/02/03 18:50:36 sebastia Exp $

COMMENT=		HTML, XML, SAX and Reader parser

DISTNAME=		nokogiri-1.11.1
CATEGORIES=		textproc

HOMEPAGE=		http://nokogiri.org/

MAINTAINER =		Jeremy Evans <jeremy@openbsd.org>

# MIT
PERMIT_PACKAGE=	Yes

WANTLIB=		exslt xml2 xslt gcrypt gpg-error
LIB_DEPENDS=		textproc/libxslt

MODULES=		lang/ruby

FLAVOR ?=

.if ${FLAVOR:Mruby26}
BUILD_DEPENDS +=	${RUN_DEPENDS}
RUN_DEPENDS +=		devel/ruby-racc,${MODRUBY_FLAVOR}
.endif

CONFIGURE_STYLE=	ruby gem ext

CONFIGURE_ARGS=		--use-system-libraries \
			--with-xml2-include=${LOCALBASE}/include/libxml2/

.include <bsd.port.mk>
