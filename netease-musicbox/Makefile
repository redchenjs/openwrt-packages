include $(TOPDIR)/rules.mk

PKG_NAME:=netease-musicbox
PKG_VERSION:=0.2.5.4
PKG_RELEASE:=1

PYPI_NAME:=NetEase-MusicBox
PKG_HASH:=fa4cffafff6ac40598a892661e81c80a77ba7e3cf051c2d98ee557e184a34b08

PKG_MAINTAINER:=
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE.txt

PYTHON_DIR:=$(TOPDIR)/feeds/packages/lang/python

include $(PYTHON_DIR)/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(PYTHON_DIR)/python3-package.mk

define Package/netease-musicbox
	SECTION:=multimedia
	CATEGORY:=Multimedia
	TITLE:=NetEase-MusicBox
	URL:=https://github.com/darknessomi/musicbox
	DEPENDS:= \
	  +mpg123 +aria2 \
	  +python3-future \
	  +python3-webbrowser \
	  +python3-cryptodomex \
	  +python3-pkg-resources \
	  +python3-requests-cache
	VARIANT:=python3
endef

$(eval $(call Py3Package,netease-musicbox))
$(eval $(call BuildPackage,netease-musicbox))
