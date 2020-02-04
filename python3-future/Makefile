include $(TOPDIR)/rules.mk

PKG_NAME:=python3-future
PKG_VERSION:=0.18.2
PKG_RELEASE:=1

PYPI_NAME:=future
PKG_HASH:=b1bead90b70cf6ec3f0710ae53a525360fa360d306a86583adc6bf83a4db537d

PKG_MAINTAINER:=
PKG_LICENSE:=
PKG_LICENSE_FILES:=

PYTHON_DIR:=$(TOPDIR)/feeds/packages/lang/python

include $(PYTHON_DIR)/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(PYTHON_DIR)/python3-package.mk

define Package/python3-future
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python3-future
	VARIANT:=python3
endef

$(eval $(call Py3Package,python3-future))
$(eval $(call BuildPackage,python3-future))
