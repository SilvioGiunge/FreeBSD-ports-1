# Created by: Boris Samorodov <bsam@FreeBSD.org>
# $FreeBSD$

CATEGORIES=	devel python
DISTNAME=	${PORTNAME}-${PORTVERSION}

BUILD_DEPENDS=	${PYTHON_SITELIBDIR}/PyQt4/QtGui.so:x11-toolkits/py-qt4-gui \
		${PYTHON_SITELIBDIR}/PyQt4/Qsci.so:devel/py-qt4-qscintilla2
RUN_DEPENDS:=	${BUILD_DEPENDS} \
		${PYTHON_SITELIBDIR}/PyQt4/QtNetwork.so:net/py-qt4-network \
		${PYTHON_SITELIBDIR}/PyQt4/QtSvg.so:graphics/py-qt4-svg \
		${PYTHON_SITELIBDIR}/PyQt4/QtSql.so:databases/py-qt4-sql \
		${PYTHON_SITELIBDIR}/PyQt4/QtWebKit.so:www/py-qt4-webkit \
		${PYTHON_SITELIBDIR}/PyQt4/QtHelp.so:devel/py-qt4-help \
		${PYTHON_LIBDIR}/lib-dynload/_sqlite3.so:databases/py-sqlite3

USES=		desktop-file-utils
INSTALL_CMD=	install.py -c -f eric6config.freebsd -i ${STAGEDIR}
PLIST_FILES=
SUB_FILES=	eric6.desktop
OPTIONS_DEFINE=	DOCS EXAMPLES
EXTRA_PATCHES=
MASTERPORT=

PORTDATA=	*
PORTDOCS=	*
PORTEXAMPLES=	*

do-configure:
	${SED}  -e 's,PYTHON_SITELIBDIR,${PYTHON_SITELIBDIR},' \
		-e 's,PREFIX,${PREFIX},' \
		-e 's,DATADIR,${DATADIR},' \
		-e 's,LOCALBASE,${LOCALBASE},' \
		-e 's,DOCSDIR,${DOCSDIR},' \
		-e 's,EXAMPLESDIR,${EXAMPLESDIR},' \
		< ${FILESDIR}/config > ${WRKSRC}/eric6config.freebsd

post-install:
	${INSTALL_DATA} ${WRKDIR}/eric6.desktop ${STAGEDIR}${PREFIX}/share/applications/
	${LN} -sf ${DATADIR}/icons/default/eric.png ${STAGEDIR}${PREFIX}/share/pixmaps/eric6.png
	@${MKDIR} ${STAGEDIR}${DATADIR}/i18n

.include "${.CURDIR}/../../devel/eric6/Makefile.inc"
