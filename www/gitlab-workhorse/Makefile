# Created by: Torsten Zuehlsdorff <ports@toco-domains.de
# $FreeBSD$

PORTNAME=	gitlab-workhorse
PORTVERSION=	0.6.5
CATEGORIES=	www
MASTER_SITES=	http://ports.toco-domains.de/

MAINTAINER=	ports@toco-domains.de
COMMENT=	Smart reverse proxy for GitLab

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

BUILD_DEPENDS=	go>=1.5.3:lang/go

PLIST_FILES=	bin/gitlab-workhorse \
		bin/gitlab-zip-cat \
		bin/gitlab-zip-metadata
PLIST_DIRS=	%%WWWDIR%%

post-install:
	${MKDIR} ${STAGEDIR}${PREFIX}/www/${PORTNAME}
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/gitlab-workhorse
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/gitlab-zip-cat
	${STRIP_CMD} ${STAGEDIR}${PREFIX}/bin/gitlab-zip-metadata

.include <bsd.port.mk>
