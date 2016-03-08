# ifeatureNew ports collection makefile for:	wordpress-plugins
# Date created:		2010-02-18
# Whom:			whitekid@gmail.com
#
# $FreeBSD$
#

PORTNAME=	wordpress-plugins
PORTVERSION=	20160303
CATEGORIES=	www
MASTER_SITES=	http://downloads.wordpress.org/plugin/
DIST_SUBDIR=	wordpress

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Wordpress plugin collection

USES=		zip

RUN_DEPENDS=	wordpress>=0:${PORTSDIR}/www/wordpress

OPTIONS_DEFINE=	\
		ADV_MANAGER \
		AJAX_PLUGIN_HELPER \
		ALL_IN_ONE_SEO_PACK \
		AUTOLINK_URI \
		BROKENLINK_CHECKER \
		BRUTE_PROTECT \
		CONTACT_FORM_7 \
		DISQUS \
		ENHANCED_META \
		FOOTNOTES \
		GOOGLE_ANALYTICATOR \
		LAZY_SOCIAL_BUTTON \
		LIGHTBOX_PLUS \
		SIMPLE_TOC \
		STATS \
		SUPER_CACHE \
		SYNTAXHIGHLIGHT \
		TOC \
		WPTOUCH

OPTIONS_DEFAULT=	${OPTIONS_DEFINE}

ADV_MANAGER_DESC	= Enable Advertising Manager plugin
AJAX_PLUGIN_HELPER_DESC	= Enable Ajax Plugin Helper plugin
ALL_IN_ONE_SEO_PACK_DESC= Enable All in One SEO Pack plugin
AUTOLINK_URI_DESC	= Enable Autolink URI plugin
BROKENLINK_CHECKER_DESC	= Enable Broken Link Checker plugin
BRUTE_PROTECT_DESC	= Enable BruteProtect
CONTACT_FORM_7_DESC	= Enable Contact form 7 plugin
DISQUS_DESC		= Enable Disqus Comment System plugin
ENHANCED_META_DESC	= Enable Enhanced meta plugin
FOOTNOTES_DESC		= Enable Footnotes plugin
GOOGLE_ANALYTICATOR_DESC= Enable Google Analyticator plugin
LAZY_SOCIAL_BUTTON_DESC	= Enable Lazy Social Buttons
LIGHTBOX_PLUS_DESC	= Enable Lightbox Plus plugin
SIMPLE_TOC_DESC		= Enable Bainternet Simple TOC plugin
STATS_DESC		= Enable WordPress.com Stats plugin
SUPER_CACHE_DESC	= Enable WP Super Cache plugin
SYNTAXHIGHLIGHT_DESC	= Enable SyntaxHighlighter Envolved plugin
TOC_DESC		= Enable TOC plugin
TWEET_BUTTON_DESC	= Enable WP Tweet Button plugin
WPTOUCH_DESC		= Enable WPTouch plugin

NO_BUILD?=	yes
WRKSRC?=	${WRKDIR}
PLIST=		${WRKDIR}/pkg-plist

.include <bsd.port.options.mk>

.if ${PORT_OPTIONS:MADV_MANAGER}
DISTFILES+=	advertising-manager.3.5.3.zip
.endif

.if ${PORT_OPTIONS:MAJAX_PLUGIN_HELPER}
DISTFILES+=	ajax-plugin-helper.1.0.5.zip
.endif

.if ${PORT_OPTIONS:MALL_IN_ONE_SEO_PACK}
DISTFILES+=	all-in-one-seo-pack.2.3.2.3.zip
.endif

.if ${PORT_OPTIONS:MAUTOLINK_URI}
DISTFILES+=	sem-autolink-uri.zip
.endif

.if ${PORT_OPTIONS:MBROKENLINK_CHECKER}
DISTFILES+=	broken-link-checker.1.10.11.zip
.endif

.if ${PORT_OPTIONS:MBRUTE_PROTECT}
DISTFILES+=	bruteprotect.zip
.endif

.if ${PORT_OPTIONS:MCONTACT_FORM_7}
DISTFILES+=	contact-form-7.4.4.zip
.endif

.if ${PORT_OPTIONS:MDISQUS}
DISTFILES+=	disqus-comment-system.zip
.endif

.if ${PORT_OPTIONS:MENHANCED_META}
DISTFILES+=	enhanced-meta-widget.3.0.0.zip
.endif

.if ${PORT_OPTIONS:MFOOTNOTES}
DISTFILES+=	footnotes-for-wordpress.2010.0822.zip
.endif

.if ${PORT_OPTIONS:MGOOGLE_ANALYTICATOR}
DISTFILES+=	google-analyticator.zip
.endif

.if ${PORT_OPTIONS:MLAZY_SOCIAL_BUTTON}
DISTFILES+=	lazy-social-buttons.1.0.7.zip
.endif

.if ${PORT_OPTIONS:MLIGHTBOX_PLUS}
DISTFILES+=	lightbox-plus.2.7.2.zip
.endif

.if ${PORT_OPTIONS:MSIMPLE_TOC}
DISTFILES+=	bainternet-simple-toc.0.8.1.zip
.endif

.if ${PORT_OPTIONS:MSTATS}
DISTFILES+=	stats.zip
.endif

.if ${PORT_OPTIONS:MSUPER_CACHE}
DISTFILES+=	wp-super-cache.1.4.8.zip
.endif

.if ${PORT_OPTIONS:MSYNTAXHIGHLIGHT}
DISTFILES+=	syntaxhighlighter.zip
.endif

.if ${PORT_OPTIONS:MTOC}
DISTFILES+=	toc-for-wordpress.zip
.endif

.if ${PORT_OPTIONS:MWPTOUCH}
DISTFILES+=	wptouch.4.0.4.zip
.endif

PLUGIN_DIR=	${PREFIX}/www/wordpress/wp-content/plugins
PLUGINS_DIRS=	${DISTFILES:C|\.[\.0-9]*zip||}

post-patch:
	@${RM} -f ${PLIST}

.for f in ${PLUGINS_DIRS}
	@cd ${WRKSRC} && \
	${FIND} -s ${f} -type f | ${SED} -e 's|^|${PLUGIN_DIR}/|' >> ${PLIST} && \
	${FIND} -d ${f} -type d | ${SED} -e 's|^|@dirrm ${PLUGIN_DIR}/|' >> ${PLIST}
.endfor

do-install:
.for f in ${PLUGINS_DIRS}
	@cd ${WRKSRC} && \
	${FIND} ${f} -type d -exec ${MKDIR} ${STAGEDIR}${PLUGIN_DIR}/{} \; && \
	${FIND} ${f} -type f -exec ${CP} {} ${STAGEDIR}${PLUGIN_DIR}/{} \;
.endfor

.include <bsd.port.mk>
