# Created by Choe, Cheng-Dae <whitekid@gmail.com>
# $FreeBSD$

PORTNAME=	wordpress-plugins
PORTVERSION=	20160316
CATEGORIES=	www
MASTER_SITES=	http://downloads.wordpress.org/plugin/
DIST_SUBDIR=	wordpress

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Wordpress plugin collection

USES=		zip

RUN_DEPENDS=	wordpress>=0:${PORTSDIR}/www/wordpress

NO_BUILD?=	yes
WRKSRC?=	${WRKDIR}
PLIST=		${WRKDIR}/pkg-plist

DISTFILES= \
	advertising-manager.3.5.3.zip \
	ajax-plugin-helper.1.0.5.zip \
	all-in-one-seo-pack.2.3.2.3.zip \
	bainternet-simple-toc.0.8.1.zip \
	broken-link-checker.1.10.11.zip \
	bruteprotect.zip \
	contact-form-7.4.4.zip \
	disable-comments.zip \
	disqus-comment-system.zip \
	enhanced-meta-widget.3.0.0.zip \
	footnotes-for-wordpress.2010.0822.zip \
	google-analyticator.6.4.9.7.zip \
	lazy-social-buttons.1.0.7.zip \
	lightbox-plus.2.7.2.zip \
	sem-autolink-uri.zip \
	stats.zip \
	syntaxhighlighter.zip \
	toc-for-wordpress.zip \
	wordfence.6.0.24.zip \
	wp-super-cache.1.4.8.zip \
	wptouch.4.0.4.zip

PLUGIN_DIR=	${PREFIX}/www/wordpress/wp-content/plugins
PLUGINS=	${DISTFILES:C|\.[\.0-9]*zip||}

post-patch:
	@${RM} -f ${PLIST}

.for f in ${PLUGINS}
	@cd ${WRKSRC} && \
	${FIND} -s ${f} -type f | ${SED} -e 's|^|${PLUGIN_DIR}/|' >> ${PLIST} && \
	${FIND} -d ${f} -type d | ${SED} -e 's|^|@dirrm ${PLUGIN_DIR}/|' >> ${PLIST}
.endfor

do-install:
.for f in ${PLUGINS}
	@cd ${WRKSRC} && \
	${FIND} ${f} -type d -exec ${MKDIR} ${STAGEDIR}${PLUGIN_DIR}/{} \; && \
	${FIND} ${f} -type f -exec ${CP} {} ${STAGEDIR}${PLUGIN_DIR}/{} \;
.endfor

.include <bsd.port.mk>
