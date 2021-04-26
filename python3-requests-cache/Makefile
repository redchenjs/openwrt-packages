include $(TOPDIR)/rules.mk

PKG_NAME:=python3-requests-cache
PKG_VERSION:=0.5.2
PKG_RELEASE:=1

PYPI_NAME:=requests-cache
PKG_HASH:=813023269686045f8e01e2289cc1e7e9ae5ab22ddd1e2849a9093ab3ab7270eb

PKG_MAINTAINER:=
PKG_LICENSE:=
PKG_LICENSE_FILES:=

PYTHON_DIR:=$(TOPDIR)/feeds/packages/lang/python

include $(PYTHON_DIR)/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(PYTHON_DIR)/python3-package.mk

define Package/python3-requests-cache
	SECTION:=lang
	CATEGORY:=Languages
	SUBMENU:=Python
	TITLE:=python3-requests-cache
	DEPENDS:=+python3-requests
endef

$(eval $(call Py3Package,python3-requests-cache))
$(eval $(call BuildPackage,python3-requests-cache))
