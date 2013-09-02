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
PORTVERSION=	20130820
CATEGORIES=	www
MASTER_SITES=	http://downloads.wordpress.org/plugin/
DIST_SUBDIR=	wordpress

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Wordpress plugin collection

RUN_DEPENDS=	wordpress>=0:${PORTSDIR}/www/wordpress

OPTIONS_DEFINE=	AKISMET \
		AJAX_PLUGIN_HELPER \
		AUTOLINK_URI \
		BROKENLINK_CHECKER \
		ENHANCED_META \
		LIGHTBOX_PLUS \
		SYNTAXHIGHLIGHT \
		STATS \
		SUPER_CACHE \
		TWEET_BUTTON \
		ALL_IN_ONE_SEO_PACK \
		CONTACT_FORM_7 \
		GOOGLE_ANALYTICATOR \
		FOOTNOTES \
		WPTOUCH \
		TOC \
		DISQUS \
		LAZY_SOCIAL_BUTTON \
		BRUTE_PROTECT

AKISMET_DESC		= Enable Akismet plugin
AJAX_PLUGIN_HELPER_DESC	= Enable Ajax Plugin Helper plugin
AUTOLINK_URI_DESC	= Enable Autolink URI plugin
BROKENLINK_CHECKER_DESC	= Enable Broken Link Checker plugin
ENHANCED_META_DESC	= Enable Enhanced meta plugin
LIGHTBOX_PLUS_DESC	= Enable Lightbox Plus plugin
SYNTAXHIGHLIGHT_DESC	= Enable SyntaxHighlighter Envolved plugin
STATS_DESC		= Enable WordPress.com Stats plugin
SUPER_CACHE_DESC	= Enable WP Super Cache plugin
TWEET_BUTTON_DESC	= Enable WP Tweet Button plugin
ALL_IN_ONE_SEO_PACK_DESC= Enable All in One SEO Pack plugin
CONTACT_FORM_7_DESC	= Enable Contact form 7 plugin
GOOGLE_ANALYTICATOR_DESC= Enable Google Analyticator plugin
FOOTNOTES_DESC		= Enable Footnotes for WordPress plugin
WPTOUCH_DESC		= Enable WPTouch for WordPress plugin
TOC_DESC		= Enable TOC for WordPress plugin
DISQUS_DESC		= Enable Disqus Comment System plugin
LAZY_SOCIAL_BUTTON_DESC	= Enable Lazy Social Buttons
BRUTE_PROTECT_DESC	= Enable BruteProtect

NO_BUILD?=	yes
WRKSRC?=	${WRKDIR}
PLIST=		${WRKDIR}/plist

#.include <bsd.port.pre.mk>
.include <bsd.port.options.mk>

WORDPRESS?=	www/wordpress

.if ${PORT_OPTIONS:MAKISMET}
DISTFILES+=	akismet.2.5.9.zip
.endif

.if ${PORT_OPTIONS:MAJAX_PLUGIN_HELPER}
DISTFILES+=	ajax-plugin-helper.1.0.5.zip
.endif

.if ${PORT_OPTIONS:MAUTO_LINK_URI}
DISTFILES+=	sem-autolink-uri.zip
.endif

.if ${PORT_OPTIONS:MBROKENLINK_CHECKER}
DISTFILES+=	broken-link-checker.1.8.3.zip
.endif

.if ${PORT_OPTIONS:MENHANCED_META}
DISTFILES+=	enhanced-meta-widget.3.0.0.zip
.endif

.if ${PORT_OPTIONS:MLIGHTBOX_PLUS}
DISTFILES+=	lightbox-plus.2.6.zip
.endif

.if ${PORT_OPTIONS:MSYNTAXHIGHLIGHT}
DISTFILES+=	syntaxhighlighter.zip
.endif

.if ${PORT_OPTIONS:MWPTOUCH}
DISTFILES+=	wptouch.1.9.41.zip
.endif

.if ${PORT_OPTIONS:MSTATS}
DISTFILES+=	stats.zip
.endif

.if ${PORT_OPTIONS:MSUPER_CACHE}
DISTFILES+=	wp-super-cache.1.3.2.zip
.endif

.if ${PORT_OPTIONS:MTWEET_BUTTON}
DISTFILES+=	wp-tweet-button.zip
.endif

.if ${PORT_OPTIONS:MALL_IN_ONE_SEO_PACK}
DISTFILES+=	all-in-one-seo-pack.2.0.3.zip
.endif

.if ${PORT_OPTIONS:MCONTACT_FORM_7}
DISTFILES+=	contact-form-7.3.5.2.zip
.endif

.if ${PORT_OPTIONS:MGOOGLE_ANALYTICATOR}
DISTFILES+=	google-analyticator.zip
.endif

.if ${PORT_OPTIONS:MFOOTNOTES}
DISTFILES+=	footnotes-for-wordpress.2010.0822.zip
.endif

.if ${PORT_OPTIONS:MTOC}
DISTFILES+=	toc-for-wordpress.zip
.endif

.if ${PORT_OPTIONS:MDISQUS}
DISTFILES+=	disqus-comment-system.2.74.zip
.endif

.if ${PORT_OPTIONS:MLAZY_SOCIAL_BUTTON}
DISTFILES+=	lazy-social-buttons.1.0.7.zip
.endif
       
.if ${PORT_OPTIONS:MBRUTE_PROTECT}
DISTFILES+=	bruteprotect.zip
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

#.include <bsd.port.post.mk>
.include <bsd.port.mk>
