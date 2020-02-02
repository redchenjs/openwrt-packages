include $(TOPDIR)/rules.mk

PKG_NAME:=shadowsocksr-libev
PKG_VERSION:=2.5.6
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/shadowsocksrr/shadowsocksr-libev
PKG_SOURCE_VERSION:=4799b312b8244ec067b8ae9ba4b85c877858976c
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.xz

PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_USE_MIPS16:=0
PKG_BUILD_PARALLEL:=1
PKG_BUILD_DEPENDS:=c-ares pcre

include $(INCLUDE_DIR)/package.mk

define Package/shadowsocksr-libev/Default
  define Package/shadowsocksr-libev-ssr-$(1)
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=Web Servers/Proxies
	TITLE:=shadowsocksr-libev ssr-$(1)
	URL:=https://github.com/shadowsocksrr/shadowsocksr-libev
	DEPENDS:=+libev +libmbedtls +libpthread +libsodium $(DEPENDS_ssr-$(1))
  endef

  define Package/shadowsocksr-libev-ssr-$(1)/install
	$$(INSTALL_DIR) $$(1)/usr/bin
	$$(INSTALL_BIN) $$(PKG_INSTALL_DIR)/usr/bin/ss-$(1) $$(1)/usr/bin/ssr-$(1)
  endef
endef

DEPENDS_ssr-local = +libpcre
DEPENDS_ssr-server = +libcares +libpcre

SHADOWSOCKSR_COMPONENTS:=local redir check server
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

TARGET_CFLAGS += -flto
TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed

$(foreach component,$(SHADOWSOCKSR_COMPONENTS), \
  $(eval $(call BuildPackage,shadowsocksr-libev-ssr-$(component))) \
)
$(eval $(call BuildPackage,shadowsocksr-libev-ssr-tunnel))
