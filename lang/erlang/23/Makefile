# $OpenBSD: Makefile,v 1.5 2020/05/04 08:45:15 kmos Exp $

BROKEN-alpha=	beam/erl_process.c:6692: internal compiler error: in final_scan_insn, at final.c:2449

COMMENT-main=	${COMMENT}
COMMENT-wx=	WxWidgets bindings for Erlang

V=		23.0
MAJ_V=		23
EPOCH=		0
DISTNAME=	otp_src_$V
PKGNAME=	erlang-$V
PKGNAME-main=	erlang-$V
PKGNAME-wx=	erlang-wx-$V

REVISION-main=	0
REVISION-wx=	0

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

AUTOCONF_VERSION =2.59
CONFIGURE_ENV =         LDFLAGS="${LDFLAGS} -pthread"
AUTOCONF_DIR =          ${WRKSRC}/erts \
			${WRKSRC}/lib/wx/

MODGNU_CONFIG_GUESS_DIRS ?=     ${WRKSRC}/erts/autoconf \
				${WRKSRC}/lib/erl_interface/src/auxdir \
				${WRKSRC}/lib/wx/autoconf

# Use the target 'gen-versions' to update this list
ERL_VERSIONS=	\
ASN1_VSN        5.0.13 \
COMMON_TEST_VSN 1.19 \
COMPILER_VSN    7.6 \
CRYPTO_VSN      4.7 \
DEBUGGER_VSN    5.0 \
DIALYZER_VSN    4.2 \
DIAMETER_VSN    2.2.3 \
EDOC_VSN        0.12 \
EI_VSN  4.0 \
ELDAP_VSN       1.2.8 \
EMACS_VSN       2.7.0 \
ERL_DOCGEN_VSN  1.0 \
ERL_INTERFACE_VSN       4.0 \
ET_VSN  1.6.4 \
EUNIT_VSN       2.5 \
FTP_VSN 1.0.4 \
HIPE_VSN        4.0 \
INETS_VSN       7.2 \
JINTERFACE_VSN  1.11 \
KERNEL_VSN      7.0 \
MEGACO_VSN      3.19 \
MNESIA_VSN      4.17 \
OBSERVER_VSN    2.9.4 \
ODBC_VSN        2.13 \
OS_MON_VSN      2.5.2 \
PARSETOOLS_VSN  2.2 \
PUBLIC_KEY_VSN  1.8 \
RELTOOL_VSN     0.8 \
RUNTIME_TOOLS_VSN       1.15 \
SASL_VSN        4.0 \
SNMP_VSN        5.6 \
SSH_VSN 4.10 \
SSL_VSN 10.0 \
STDLIB_VSN      3.13 \
SYNTAX_TOOLS_VSN        2.3 \
TFTP_VSN        1.0.2 \
TOOLS_VSN       3.4 \
WX_VSN  1.9.1 \
XMERL_VSN       1.3.25 \
ERTS_VSN        11.0
SYSTEM_VSN=	${V:R}

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

.include <bsd.port.mk>
