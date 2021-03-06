include $(TOPDIR)/rules.mk

PKG_NAME:=fullconenat
PKG_RELEASE:=1

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_URL:=https://github.com/Chion82/netfilter-full-cone-nat
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2020-02-03
PKG_SOURCE_VERSION:=0cf3b48fd7d2fa81d0297d1fff12bbd0580fc435
PKG_MIRROR_HASH:=994e8403cb4585e72c42cca367ddd7450f4bbde0c17333ad6ba42bea624ea222

PKG_MAINTAINER:=
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define Package/iptables-mod-fullconenat
	SUBMENU:=Firewall
	SECTION:=net
	CATEGORY:=Network
	TITLE:=FULLCONENAT iptables extension
	DEPENDS:=+iptables +kmod-ipt-fullconenat
	MAINTAINER:=Chion Tang <tech@chionlab.moe>
endef

define Package/iptables-mod-fullconenat/install
	$(INSTALL_DIR) $(1)/usr/lib/iptables
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/libipt_FULLCONENAT.so $(1)/usr/lib/iptables
	$(INSTALL_DIR) $(1)/usr/share/fullconenat
	$(INSTALL_DATA) ./files/firewall.include $(1)/usr/share/fullconenat
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_BIN) ./files/fullconenat.defaults $(1)/etc/uci-defaults/
endef

define Package/iptables-mod-fullconenat/prerm
#!/bin/sh
uci -q batch <<-EOF
	delete firewall.fullconenat
	commit firewall
EOF
endef

define KernelPackage/ipt-fullconenat
	SUBMENU:=Netfilter Extensions
	TITLE:=FULLCONENAT netfilter module
	DEPENDS:=+kmod-nf-ipt +kmod-nf-nat
	MAINTAINER:=Chion Tang <tech@chionlab.moe>
	KCONFIG:=CONFIG_NF_CONNTRACK_EVENTS=y CONFIG_NF_CONNTRACK_CHAIN_EVENTS=y
	FILES:=$(PKG_BUILD_DIR)/xt_FULLCONENAT.ko
	AUTOLOAD:=$(call AutoProbe,xt_FULLCONENAT)
endef

include $(INCLUDE_DIR)/kernel-defaults.mk

define Build/Prepare
	$(call Build/Prepare/Default)
	$(CP) ./files/Makefile $(PKG_BUILD_DIR)/
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
        CROSS_COMPILE="$(TARGET_CROSS)" \
        ARCH="$(LINUX_KARCH)" \
        M="$(PKG_BUILD_DIR)" \
        modules
	$(call Build/Compile/Default)
endef

$(eval $(call BuildPackage,iptables-mod-fullconenat))
$(eval $(call KernelPackage,ipt-fullconenat))
