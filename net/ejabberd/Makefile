COMMENT =	Robust, Ubiquitous and Massively Scalable Messaging Platform

V =		20.04
DISTNAME =	$V
PKGNAME =	ejabberd-$V
CATEGORIES =	net

HOMEPAGE =	https://ejabberd.im/

MAINTAINER =	Mathieu Kerjouan <niamkik@protonmail.com>

PERMIT_PACKAGE = Yes

BUILD_DEPENDS += lang/erlang/21 
BUILD_DEPENDS += devel/git
BUILD_DEPENDS += devel/automake/1.16
BUILD_DEPENDS += devel/autoconf/2.69

DEPENDS +=	libyaml

ERL=		/usr/local/bin/erl21
ERLC=		/usr/local/bin/erlc21

# WANTLIB +=	yaml
CONFIGURE_STYLE = autoreconf gnu
AUTOCONF_VERSION = 2.69
AUTOMAKE_VERSION = 1.16
MAKE_ENV =	${CONFIGURE_ENV}
USE_GMAKE =	Yes

EXTRACT_SUFX =	.tar.gz
WRKDIST =	${WRKDIR}/${PKGNAME}

MASTER_SITES =	https://github.com/processone/ejabberd/archive/

_CFLAGS += 	-I/usr/local/include
_CPPFLAGS +=	-I/usr/local/include
_LDFLAGS +=	-L/usr/local/lib

CONFIGURE_FLAGS += --enable-user=_ejabberd
CONFIGURE_FLAGS += --enable-group=_ejabberd

CONFIGURE_ARGS=	--bindir=/usr/local/bin \
		--sbindir=/usr/local/sbin \
		--libexecdir=/usr/local/libexec/ejabberd \
		--libdir=/usr/local/lib/ejabberd \
		--datarootdir=/usr/local/share/ejabberd

CONFIGURE_ENV=	CPPFLAGS=$(_CPPFLAGS) \
		LDFLAGS=$(_LDFLAGS) \
		ERL=$(ERL) \
		ERLC=$(ERLC) \
		CFLAGS=$(_CFLAGS) \
		HOME=${WRKDIST}

do-test:
	make test

post-install:
	chmod +x ${PREFIX}/sbin/ejabberdctl
	${INSTALL_DATA} ejabberd.yml.example ${PREFIX}/etc/ejabberd/
	mkdir -p ${PREFIX}/var/ejabberd

.include <bsd.port.mk>

.if ${FLAVOR:Mmysql}
CONFIGURE_FLAGS += --enable-mysql
.endif

.if ${FLAVOR:Mpostgresql}
CONFIGURE_FLAGS += --enable-pgsql
.endif

.if ${FLAVOR:Msqlite}
CONFIGURE_FLAGS += --enable-sqlite
.endif

.if ${FLAVOR:Mdebug}
CONFIGURE_FLAGS += --debug
.endif

.if ${FLAVOR:Mredis}
CONFIGURE_FLAGS += --enable-rediS
.endif
