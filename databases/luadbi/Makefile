# Created by: Olexander Melnyk <olexander.v.melnyk@gmail.com>
# $FreeBSD$

PORTNAME=	luadbi
PORTVERSION=	0.5
PORTREVISION=	2
CATEGORIES=	databases
MASTER_SITES=	GOOGLE_CODE
DISTNAME=	${PORTNAME}.${PORTVERSION}

MAINTAINER=	olexander.v.melnyk@gmail.com
COMMENT=	LuaDBI driver

LICENSE=	MIT

NO_WRKSUBDIR=	yes

USES=		gmake lua:51 shebangfix
SHEBANG_FILES=	DBI.lua

CFLAGS+=	-fpic -I${LOCALBASE}/include -I${LUA_INCDIR} -I. \
		-I${LOCALBASE}/include/postgresql/server
LDFLAGS+=	-shared -L${LOCALBASE}/lib -L${LUA_LIBDIR}
MAKE_ENV+=	COMMON_LDFLAGS="${LDFLAGS}"

OPTIONS_MULTI=	DATABASE
OPTIONS_MULTI_DATABASE=	MYSQL SQLITE3 PGSQL
OPTIONS_DEFAULT=	MYSQL

PLIST_FILES=	%%LUA_MODSHAREDIR%%/DBI.lua

MYSQL_USE=		MYSQL=yes
MYSQL_LDFLAGS=		-L ${LOCALBASE}/lib/mysql
MYSQL_CFLAGS=		-I ${LOCALBASE}/include/mysql
MYSQL_ALL_TARGET=	mysql
MYSQL_PLIST_FILES=	%%LUA_MODLIBDIR%%/dbdmysql.so

SQLITE3_USE=		SQLITE=3
SQLITE3_ALL_TARGET=	sqlite3
SQLITE3_PLIST_FILES=	%%LUA_MODLIBDIR%%/dbdsqlite3.so

PGSQL_USES=		pgsql
PGSQL_ALL_TARGET=	psql
PGSQL_PLIST_FILES=	%%LUA_MODLIBDIR%%/dbdpostgresql.so

do-install:
	@${MKDIR} ${STAGEDIR}${LUA_MODLIBDIR}
	@${MKDIR} ${STAGEDIR}${LUA_MODSHAREDIR}
	${CP} ${WRKSRC}/DBI.lua ${STAGEDIR}${LUA_MODSHAREDIR}

do-install-MYSQL-on:
	${INSTALL_PROGRAM} ${WRKSRC}/dbdmysql.so ${STAGEDIR}${LUA_MODLIBDIR}

do-install-SQLITE3-on:
	${INSTALL_PROGRAM} ${WRKSRC}/dbdsqlite3.so ${STAGEDIR}${LUA_MODLIBDIR}

do-install-PGSQL-on:
	${INSTALL_PROGRAM} ${WRKSRC}/dbdpostgresql.so ${STAGEDIR}${LUA_MODLIBDIR}

.include <bsd.port.mk>
