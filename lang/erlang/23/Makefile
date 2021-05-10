# $OpenBSD: Makefile,v 1.5 2020/05/04 08:45:15 kmos Exp $

COMMENT-main=	${COMMENT}
COMMENT-wx=	WxWidgets bindings for Erlang

V=		23.3.4
MAJ_V=		23
EPOCH=		2
DISTNAME=	otp_src_$V
PKGNAME=	erlang-$V
PKGNAME-main=	erlang-$V
PKGNAME-wx=	erlang-wx-$V

REVISION-main=	2
REVISION-wx=	2

VERSION_SPEC=	>=23v0,<24v0
PKGSPEC-main=	erlang-${VERSION_SPEC}
PKGSPEC-wx=	erlang-wx-${VERSION_SPEC}

BUILD_DEPENDS+=	textproc/libxslt

COMPILER= base-clang
CONFIGURE_STYLE = configure
CONFIGURE_ARGS+=--without-jinterface	\
		--without-odbc		\
		--enable-threads	\
		--enable-kernel-poll	\
		--disable-hipe		\
		CC=cc CXX=c++

MULTI_PACKAGES = -main -wx

WANTLIB =	m pthread
WANTLIB-main =	${WANTLIB} c crypto kvm curses util

WANTLIB-wx += ${WANTLIB} GL GLU ${COMPILER_LIBCXX}
WANTLIB-wx += wx_baseu-3.0 wx_baseu_xml-3.0 wx_gtk3u_adv-3.0 wx_gtk3u_aui-3.0
WANTLIB-wx += wx_gtk3u_core-3.0 wx_gtk3u_gl-3.0 wx_gtk3u_html-3.0
WANTLIB-wx += wx_gtk3u_stc-3.0 wx_gtk3u_xrc-3.0

LIB_DEPENDS-wx +=x11/wxWidgets>=2.8.12p10
RUN_DEPENDS-wx =${BASE_PKGPATH},-main>=${MAJ_V}

DOC_DIR=	${PREFIX}/lib/erlang${MAJ_V}/
FAKE_FLAGS =	libdir_suffix="/erlang${MAJ_V}"

AUTOCONF_VERSION =2.69
CONFIGURE_ENV =         LDFLAGS="${LDFLAGS} -pthread"
AUTOCONF_DIR =          ${WRKSRC}/erts \
			${WRKSRC}/lib/wx/

MODGNU_CONFIG_GUESS_DIRS ?=     ${WRKSRC}/erts/autoconf \
				${WRKSRC}/lib/erl_interface/src/auxdir \
				${WRKSRC}/lib/wx/autoconf

# Use the target 'gen-versions' to update this list
ERL_VERSIONS=	\
ASN1_VSN        5.0.15 \
COMMON_TEST_VSN 1.20.2 \
COMPILER_VSN    7.6.9 \
CRYPTO_VSN      4.9 \
DEBUGGER_VSN    5.0 \
DIALYZER_VSN    4.3.1 \
DIAMETER_VSN    2.2.4 \
EDOC_VSN        0.12 \
EI_VSN  4.0.3 \
ELDAP_VSN       1.2.9 \
EMACS_VSN       2.7.0 \
ERL_DOCGEN_VSN  1.0.2 \
ERL_INTERFACE_VSN       4.0.3 \
ET_VSN  1.6.4 \
EUNIT_VSN       2.6 \
FTP_VSN 1.0.5 \
HIPE_VSN        4.0.1 \
INETS_VSN       7.3.2 \
JINTERFACE_VSN  1.11.1 \
KERNEL_VSN      7.3.1 \
MEGACO_VSN      3.19.5 \
MNESIA_VSN      4.19 \
OBSERVER_VSN    2.9.5 \
ODBC_VSN        2.13.3 \
OS_MON_VSN      2.6.1 \
PARSETOOLS_VSN  2.2 \
PUBLIC_KEY_VSN  1.10 \
RELTOOL_VSN     0.8 \
RUNTIME_TOOLS_VSN       1.16.1 \
SASL_VSN        4.0.2 \
SNMP_VSN        5.8 \
SSH_VSN 4.11.1 \
SSL_VSN 10.3.1 \
STDLIB_VSN      3.14.2 \
SYNTAX_TOOLS_VSN        2.5 \
TFTP_VSN        1.0.2 \
TOOLS_VSN       3.4.4 \
WX_VSN  1.9.3 \
XMERL_VSN       1.3.27 \
ERTS_VSN        11.2.2
SYSTEM_VSN=	${MAJ_V}

.include <bsd.port.mk>

pre-configure:
	${SUBST_CMD} ${WRKSRC}/make/install_bin \
		${WRKSRC}/Makefile.in \
		${WRKSRC}/erts/etc/common/ct_run.c \
		${WRKSRC}/erts/etc/common/dialyzer.c \
		${WRKSRC}/erts/etc/common/erlc.c \
		${WRKSRC}/erts/etc/common/escript.c \
		${WRKSRC}/erts/etc/common/typer.c \
		${WRKSRC}/lib/dialyzer/src/dialyzer_plt.erl \
		${WRKSRC}/lib/wx/configure.in

do-configure:
	cd ${WRKSRC} && ./configure ${CONFIGURE_ARGS}

post-install:
	${INSTALL_DATA} ${WRKSRC}/AUTHORS ${PREFIX}/lib/erlang${SYSTEM_VSN}/
	${INSTALL_DATA} ${WRKSRC}/LICENSE.txt ${PREFIX}/lib/erlang${SYSTEM_VSN}/
	${INSTALL_DATA} ${WRKSRC}/system/COPYRIGHT ${PREFIX}/lib/erlang${SYSTEM_VSN}/
