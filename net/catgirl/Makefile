# $OpenBSD: Makefile,v 1.9 2021/03/24 21:37:17 kn Exp $

COMMENT =	curses TLS-only IRC client
DISTNAME =	catgirl-1.7

CATEGORIES =	net

MAINTAINER =	Solene Rapenne <solene@perso.pw> \
		Klemens Nanni <kn@openbsd.org>

HOMEPAGE =	https://git.causal.agency/catgirl

# GPLv3+
PERMIT_PACKAGE =Yes

# C11
COMPILER =	base-clang ports-gcc
COMPILER_LANGS =	c

# uses pledge() and unveil()
WANTLIB +=	c curses tls

DEBUG_PACKAGES =${BUILD_PACKAGES}

MASTER_SITES =	https://git.causal.agency/catgirl/snapshot/

NO_TEST =	Yes

FAKE_FLAGS =	PREFIX=${PREFIX} \
		MANDIR=${PREFIX}/man

EXAMPLES =	${PREFIX}/share/examples/catgirl

post-install:
	${INSTALL_DATA_DIR} ${EXAMPLES}
	${INSTALL_DATA} ${WRKSRC}/scripts/chat.tmux.conf ${EXAMPLES}/

.include <bsd.port.mk>
