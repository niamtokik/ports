# $OpenBSD: Makefile,v 1.5 2020/05/04 08:45:15 kmos Exp $

COMMENT-main=	${COMMENT}
COMMENT-wx=	WxWidgets bindings for Erlang

V=		24.0
RC=		rc3
MAJ_V=		24
EPOCH=		0
DISTNAME=	otp_src_$V-$(RC)
DISTFILES =    ${DISTNAME}.tar.gz \
                otp_doc_man_$(V)-$(RC).tar.gz
PKGNAME=	erlang-$V
PKGNAME-main=	erlang-$V
PKGNAME-wx=	erlang-wx-$V

REVISION-main=	2
REVISION-wx=	2

VERSION_SPEC=	>=24v0,<25v0
PKGSPEC-main=	erlang-${VERSION_SPEC}
PKGSPEC-wx=	erlang-wx-${VERSION_SPEC}

# Only for release candidate
MASTER_SITES = https://github.com/erlang/otp/releases/download/OTP-$(V)-$(RC)/

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
ASN1_VSN	5.1 \
COMMON_TEST_VSN	1.20.1 \
COMPILER_VSN	8.0 \
CRYPTO_VSN	5.0 \
DEBUGGER_VSN	5.1 \
DIALYZER_VSN	4.4 \
DIAMETER_VSN	2.2.3 \
EDOC_VSN	1.0 \
EI_VSN	5.0 \
ELDAP_VSN	1.2.9 \
EMACS_VSN	2.7.0 \
ERL_DOCGEN_VSN	1.1 \
ERL_INTERFACE_VSN	5.0 \
ET_VSN	1.7 \
EUNIT_VSN	2.6 \
FTP_VSN	1.1 \
INETS_VSN	7.4 \
JINTERFACE_VSN	1.12 \
KERNEL_VSN	8.0 \
MEGACO_VSN	4.0 \
MNESIA_VSN	4.19.1 \
OBSERVER_VSN	2.9.6 \
ODBC_VSN	2.13.4 \
OS_MON_VSN	2.7 \
PARSETOOLS_VSN	2.3 \
PUBLIC_KEY_VSN	1.10 \
RELTOOL_VSN	0.9 \
RUNTIME_TOOLS_VSN	1.16.1 \
SASL_VSN	4.1 \
SNMP_VSN	5.8.1 \
SSH_VSN	4.12 \
SSL_VSN	10.4 \
STDLIB_VSN	3.15 \
SYNTAX_TOOLS_VSN	2.6 \
TFTP_VSN	1.0.3 \
TOOLS_VSN	3.5 \
WX_VSN	2.0 \
XMERL_VSN	1.4 \
ERTS_VSN	12.0
SYSTEM_VSN=	${MAJ_V}

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
	ln -sf ../lib/erlang${MAJ_V}/lib/${ERL_EI}/bin/erl_call ${PREFIX}/bin/erl_call${MAJ_V}
	tar zxf ${FULLDISTDIR}/otp_doc_man_${V}-${RC}.tar.gz -C ${DOC_DIR}
	rm -r ${DOC_DIR}/man/man7/*MIB.7
	rm -r ${DOC_DIR}/man/man7/*TM.7
	if [ ! -x ${PREFIX}/lib/erlang${MAJ_V}/${ERL_ERTS}/bin/beam.smp ]; then \
		cp -v ${PREFIX}/lib/erlang${MAJ_V}/${ERL_ERTS}/bin/beam \
		${PREFIX}/lib/erlang${MAJ_V}/${ERL_ERTS}/bin/beam.smp; fi

.include <bsd.port.mk>
