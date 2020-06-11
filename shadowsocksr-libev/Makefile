include $(TOPDIR)/rules.mk

PKG_NAME:=shadowsocksr-libev
PKG_RELEASE:=1

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_URL:=https://github.com/shadowsocksrr/shadowsocksr-libev
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2020-02-03
PKG_SOURCE_VERSION:=4799b312b8244ec067b8ae9ba4b85c877858976c
PKG_MIRROR_HASH:=

PKG_MAINTAINER:=
PKG_BUILD_PARALLEL:=1

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_USE_MIPS16:=0

include $(INCLUDE_DIR)/package.mk

define Package/shadowsocksr-libev/Default
  define Package/shadowsocksr-libev-ssr-$(1)
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=Web Servers/Proxies
	TITLE:=shadowsocksr-libev ssr-$(1)
	URL:=https://github.com/shadowsocksrr/shadowsocksr-libev
	DEPENDS:=+libev +libopenssl +libpthread +libpcre $(DEPENDS_$(1))
  endef

  define Package/shadowsocksr-libev-ssr-$(1)/install
	$$(INSTALL_DIR) $$(1)/usr/bin
	$$(INSTALL_BIN) $$(PKG_INSTALL_DIR)/usr/bin/ss-$(1) $$(1)/usr/bin/ssr-$(1)
	$(INSTALL_$(1))
  endef
endef

DEPENDS_redir = +ip +ipset +iptables-mod-tproxy +resolveip
INSTALL_redir = $$(INSTALL_BIN) ./files/ss-rules $$(1)/usr/bin/ssr-rules

SHADOWSOCKSR_COMPONENTS:=local redir
define shadowsocksr-libev/templates
	$(foreach component,$(SHADOWSOCKSR_COMPONENTS),
		$(call Package/shadowsocksr-libev/Default,$(component))
	)
endef
$(eval $(call shadowsocksr-libev/templates))

define Package/shadowsocksr-libev-ssr-tunnel
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=Web Servers/Proxies
	TITLE:=shadowsocksr-libev ssr-tunnel
	URL:=https://github.com/shadowsocksrr/shadowsocksr-libev
	DEPENDS:=+shadowsocksr-libev-ssr-local
endef

define Package/shadowsocksr-libev-ssr-tunnel/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(LN) ssr-local $(1)/usr/bin/ssr-tunnel
endef

define Build/Prepare
	$(call Build/Prepare/Default)
	$(FIND) $(PKG_BUILD_DIR) \
			   -name '*.o' \
			-o -name '*.lo' \
			-o -name '.deps' \
			-o -name '.libs' \
		| $(XARGS) rm -rvf
endef

CONFIGURE_ARGS += \
	--disable-documentation \
	--disable-silent-rules \
	--disable-assert \
	--disable-ssp \

TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed

$(foreach component,$(SHADOWSOCKSR_COMPONENTS), \
	$(eval $(call BuildPackage,shadowsocksr-libev-ssr-$(component))) \
)
$(eval $(call BuildPackage,shadowsocksr-libev-ssr-tunnel))
