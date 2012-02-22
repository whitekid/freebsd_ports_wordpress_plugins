# ifeatureNew ports collection makefile for:	wordpress-plugins
# Date created:		2010-02-18
# Whom:			whitekid@gmail.com
#
# $FreeBSD$
#


#
# TODO: 이거 send-pr해야하나 sem-autolink-uri, syntaxhighlighter가 distfile에
# 버전 번호가 없어서 쪼까 거시기 함.
#

PORTNAME=	wordpress-plugins
PORTVERSION=	20120222
CATEGORIES=	www
MASTER_SITES=	http://downloads.wordpress.org/plugin/
DIST_SUBDIR=	wordpress

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Wordpress plugin collection

RUN_DEPENDS=	wordpress>=0:${PORTSDIR}/www/wordpress

OPTIONS=	AKISMET "Enable Akismet plugin" on \
		AJAX_PLUGIN_HELPER "Enable Ajax Plugin Helper plugin" on \
		AUTOLINK_URI "Enable Autolink URI plugin" on \
		BROKENLINK_CHECKER "Enable Broken Link Checker plugin" on \
		ENHANCED_META "Enable Enhanced meta plugin" on \
		LIGHTBOX_2 "Enable Lightbox 2 plugin" on \
		SYNTAXHIGHLIGHT "Enable SyntaxHighlighter Envolved plugin" on \
		STATS "Enable WordPress.com Stats plugin" on \
		SUPER_CACHE "Enable WP Super Cache plugin" on \
		TWEET_BUTTON "Enable WP Tweet Button plugin" on \
		ALL_IN_ONE_SEO_PACK "Enable All in One SEO Pack plugin" on \
		CONTACT_FORM_7 "Enable Contact form 7 plugin" on \
		GOOGLE_ANALYTICATOR "Enable Google Analyticator plugin" on

NO_BUILD?=	yes
WRKSRC?=	${WRKDIR}
PLIST=		${WRKDIR}/plist

.include <bsd.port.pre.mk>

WORDPRESS?=	www/wordpress

.if defined(WITH_AKISMET)
DISTFILES+=	akismet.2.4.0.zip
.endif

.if defined(WITH_AJAX_PLUGIN_HELPER)
DISTFILES+=	ajax-plugin-helper.1.0.5.zip
.endif

.if defined(WITH_AUTOLINK_URI)
DISTFILES+=	sem-autolink-uri.zip
.endif

.if defined(WITH_BROKENLINK_CHECKER)
DISTFILES+=	broken-link-checker.1.4.zip
.endif

.if defined(WITH_ENHANCED_META)
DISTFILES+=	enhanced-meta-widget.3.0.0.zip
.endif

.if defined(WITH_LIGHTBOX_2)
DISTFILES+=	lightbox-2.2.9.2.zip
.endif

.if defined(WITH_SYNTAXHIGHLIGHT)
DISTFILES+=	syntaxhighlighter.zip
.endif

.if defined(WITH_WPTOUCH)
DISTFILES+=	wptouch.1.9.39.zip
.endif

.if defined(WITH_STATS)
DISTFILES+=	stats.zip
.endif

.if defined(WITH_SUPER_CACHE)
DISTFILES+=	wp-super-cache.1.0.zip
.endif

.if defined(WITH_TWEET_BUTTON)
DISTFILES+=	wp-tweet-button.zip
.endif

.if defined(WITH_ALL_IN_ONE_SEO_PACK)
DISTFILES+=	all-in-one-seo-pack.1.6.13.8.zip
.endif

.if defined(WITH_CONTACT_FORM_7)
DISTFILES+=	contact-form-7.3.1.zip
.endif

.if defined(WITH_GOOGLE_ANALYTICATOR)
DISTFILES+=	google-analyticator.6.2.zip
.endif

WORDPRESS_PLUGINS?=	${WORDPRESS}/wp-content/plugins
PLUGINS_DIRS=	${DISTFILES:C|\.[\.0-9]*zip||}

pre-install:
	@${RM} -rf ${PLIST}
	@${TOUCH} ${PLIST}

.for f in ${THEME_DIRS}
	@cd ${WRKSRC} && \
	${FIND} -s ${f} -type f | ${SED} -e 's|^|${WORDPRESS_PLUGINS}/|' >> ${PLIST} && \
	${FIND} -d ${f} -type d | ${SED} -e 's|^|@dirrm ${WORDPRESS_PLUGINS}/|' >> ${PLIST}
.endfor

do-install:
.for f in ${PLUGINS_DIRS}
	@cd ${WRKSRC} && \
	${FIND} ${f} -type d -exec ${MKDIR} ${PREFIX}/${WORDPRESS_PLUGINS}/{} \; && \
	${FIND} ${f} -type f -exec ${CP} {} ${PREFIX}/${WORDPRESS_PLUGINS}/{} \;
.endfor

.include <bsd.port.post.mk>
