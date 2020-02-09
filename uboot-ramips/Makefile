include $(TOPDIR)/rules.mk

PKG_VERSION:=2020.01
PKG_RELEASE:=1

PKG_HASH:=aa453c603208b1b27bd03525775a7f79b443adec577fdc6e8f06974025a135f1

PKG_MAINTAINER:=

include $(INCLUDE_DIR)/u-boot.mk
include $(INCLUDE_DIR)/package.mk

define U-Boot/Default
	BUILD_TARGET:=ramips
endef

define U-Boot/linkit-smart-7688
	NAME:=LinkIt Smart 7688
	BUILD_SUBTARGET:=mt76x8
	BUILD_DEVICES:=mediatek_linkit-smart-7688
endef

UBOOT_MAKE_FLAGS:=

UBOOT_TARGETS:=linkit-smart-7688

$(eval $(call BuildPackage/U-Boot))
