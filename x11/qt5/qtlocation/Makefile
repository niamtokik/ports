# $OpenBSD: Makefile,v 1.10 2021/01/19 06:16:30 rsadowski Exp $

QT5NAME =		QtLocation
COMMENT-main =		Qt5 geo positioning APIs

SHARED_LIBS +=  Qt5Location               2.0 # 5.9
SHARED_LIBS +=  Qt5Positioning            3.0 # 5.9
SHARED_LIBS +=  Qt5PositioningQuick       0.0 # 5.13

MULTI_PACKAGES =	-main -examples

WANTLIB += ${COMPILER_LIBCXX} GL Qt5Concurrent Qt5Core Qt5DBus
WANTLIB += Qt5Gui Qt5Network Qt5Qml Qt5QmlModels Qt5Quick Qt5Sql
WANTLIB += crypto icudata icui18n icuuc m ssl z

LIB_DEPENDS =		x11/qt5/qtdeclarative>=${QT5_VERSION},<${QT5_NEXT_VERSION}

RUN_DEPENDS =		x11/dbus

FLAVORS =		debug

MODQMAKE_RECURSIVE =	No

.include <bsd.port.mk>
