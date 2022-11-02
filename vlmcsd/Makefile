include $(TOPDIR)/rules.mk

PKG_NAME:=vlmcsd
PKG_RELEASE=1

PKG_LICENSE:=
PKG_LICENSE_FILES:=

PKG_SOURCE_URL:=https://github.com/Wind4/vlmcsd
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2020-03-28
PKG_SOURCE_VERSION:=e599080486478e219cd065e141d6de050a450c27
PKG_MIRROR_HASH:=

PKG_MAINTAINER:=
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/vlmcsd
	SECTION:=net
	CATEGORY:=Network
	TITLE:=KMS Emulator in C
	URL:=http://forums.mydigitallife.info/threads/50234
	DEPENDS:=+libpthread
endef

define Package/vlmcsd/prerm
#!/bin/sh
sed -i '/# vlmcsd/d' /etc/dnsmasq.conf
EOF
endef

MAKE_FLAGS += \
	-C $(PKG_BUILD_DIR)

define Package/vlmcsd/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/vlmcs $(1)/usr/bin/vlmcs
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/vlmcsd $(1)/usr/bin/vlmcsd
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/etc/vlmcsd.ini $(1)/etc/vlmcsd.ini
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/etc/vlmcsd.kmd $(1)/etc/vlmcsd.kmd
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/vlmcsd.init $(1)/etc/init.d/vlmcsd
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/vlmcsd.defaults $(1)/etc/uci-defaults/
endef

$(eval $(call BuildPackage,vlmcsd))
