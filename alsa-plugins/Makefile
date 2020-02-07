include $(TOPDIR)/rules.mk

PKG_NAME:=alsa-plugins
PKG_VERSION:=1.1.9
PKG_RELEASE:=1

PKG_LICENSE:=LGPLv2.1-or-later
PKG_LICENSE_FILES:=COPYING

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=ftp://ftp.alsa-project.org/pub/lib/ \
		http://distfiles.gentoo.org/distfiles/
PKG_HASH:=161772303da521abbbf1d91f63b470c4791392d5728f2192a42d71292078f907

PKG_MAINTAINER:=
PKG_BUILD_PARALLEL:=1

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/alsa-plugins-pulse
	SECTION:=sound
	CATEGORY:=Sound
	TITLE:=ALSA plugins (pulseaudio)
	URL:=https://www.alsa-project.org/
	DEPENDS:=+alsa-lib pulseaudio
endef

define Package/alsa-plugins-pulse/install
	$(INSTALL_DIR) $(1)/usr/lib/alsa-lib
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/alsa-lib/libasound_module_conf_pulse.so $(1)/usr/lib/alsa-lib/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/alsa-lib/libasound_module_ctl_pulse.so $(1)/usr/lib/alsa-lib/
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/alsa-lib/libasound_module_pcm_pulse.so $(1)/usr/lib/alsa-lib/
	$(INSTALL_DIR) $(1)/usr/share/alsa/alsa.conf.d
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/alsa/alsa.conf.d/50-pulseaudio.conf $(1)/usr/share/alsa/alsa.conf.d/
	$(INSTALL_DIR) $(1)/etc/alsa/conf.d
	$(LN) /usr/share/alsa/alsa.conf.d/50-pulseaudio.conf $(1)/etc/alsa/conf.d/
endef

$(eval $(call BuildPackage,alsa-plugins-pulse))
