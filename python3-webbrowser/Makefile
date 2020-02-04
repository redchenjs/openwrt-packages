include $(TOPDIR)/rules.mk

PKG_NAME:=python3-webbrowser
PKG_RELEASE:=2

PKG_MAINTAINER:=
PKG_LICENSE:=Python/2.0
PKG_LICENSE_FILES:=LICENSE

PYTHON_DIR:=$(TOPDIR)/feeds/packages/lang/python

include $(INCLUDE_DIR)/package.mk
include $(PYTHON_DIR)/python3-version.mk
include $(PYTHON_DIR)/python3-package.mk

PYTHON_VERSION:=$(PYTHON3_VERSION).$(PYTHON3_VERSION_MICRO)

PKG_BUILD_DEPENDS:=python3
PKG_BUILD_DIR:=$(BUILD_DIR)/Python-$(PYTHON_VERSION)

define Package/python3-webbrowser
	SUBMENU:=Python
	SECTION:=lang
	CATEGORY:=Languages
	URL:=https://www.python.org/
	TITLE:=Python $(PYTHON_VERSION) webbrowser
	DEPENDS:=+python3-base
endef

define Py3Package/python3-webbrowser/filespec
+|/usr/lib/python$(PYTHON_VERSION)/webbrowser.py
endef

Py3Package/python3-webbrowser/install:=:

$(eval $(call Py3Package,python3-webbrowser))
$(eval $(call BuildPackage,python3-webbrowser))
