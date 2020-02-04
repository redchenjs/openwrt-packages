include $(TOPDIR)/rules.mk

PYTHON_DIR:=$(TOPDIR)/feeds/packages/lang/python

include $(PYTHON_DIR)/python3-version.mk
include $(PYTHON_DIR)/python3-package.mk

PYTHON_VERSION:=$(PYTHON3_VERSION)
PYTHON_VERSION_MICRO:=$(PYTHON3_VERSION_MICRO)

PKG_NAME:=python3-webbrowser
PKG_VERSION:=$(PYTHON_VERSION).$(PYTHON_VERSION_MICRO)
PKG_RELEASE:=2

PKG_MAINTAINER:=
PKG_LICENSE:=Python/2.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=python3

include $(INCLUDE_DIR)/package.mk

define Package/python3-webbrowser
	SUBMENU:=Python
	SECTION:=lang
	CATEGORY:=Languages
	URL:=https://www.python.org/
	TITLE:=Python $(PYTHON_VERSION) webbrowser
	DEPENDS:=+python3-base
endef

define Build/Compile
	$(LN) $(BUILD_DIR)/Python-$(PKG_VERSION)/ipkg-install \
	      $(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)/ipkg-install
endef

define Py3Package/python3-webbrowser/filespec
	-|/usr/bin
	+|/usr/lib/python$(PYTHON_VERSION)/webbrowser.py
endef

$(eval $(call Py3Package,python3-webbrowser))
$(eval $(call BuildPackage,python3-webbrowser))
