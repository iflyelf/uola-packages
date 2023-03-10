#
# Copyright (C) 2008-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=micropython-lib
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/micropython/micropython-lib.git
PKG_SOURCE_VERSION:=0c31e0b3d712fcd21982daec8bfca48ad5527a72
PKG_SOURCE_DATE:=20220324
PKG_MIRROR_HASH:=fb796c6d648e555e3e5233a3aec84be1692199b2cbae1efd7c22caf2a8c3f8f7

PKG_MAINTAINER:=Jeffery To <jeffery.to@gmail.com>
PKG_LICENSE:=MIT PSF-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/micropython-lib
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=micropython-lib
  URL:=https://github.com/micropython/micropython-lib
  DEPENDS:=+micropython
endef

define Package/micropython-lib/description
  This is a repository of libraries designed to be useful for writing
  MicroPython applications.
endef

Build/Compile:=:

define Package/micropython-lib/install
	for dir in micropython python-ecosys python-stdlib unix-ffi; do \
		$(INSTALL_DIR) $(1)/usr/lib/micropython/$$$$dir ; \
		$(CP) $(PKG_BUILD_DIR)/$$$$dir/* $(1)/usr/lib/micropython/$$$$dir/ ; \
	done
	$(FIND) $(1)/usr/lib/micropython \
		-not -type d \( -not -name '*.py' -o -name 'test_*' -o -name 'setup.py' \) -delete
	$(FIND) $(1)/usr/lib/micropython -mindepth 1 -empty -type d -delete
endef

$(eval $(call BuildPackage,micropython-lib))
