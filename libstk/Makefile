#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libstk
PKG_VERSION:=4.5.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/thestk/stk.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=1799064d6fb0cc01e4137b0e10b9731266c7d258
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_MIRROR_MD5SUM:=

PKG_LICENSE:=PERMISSIVE

include $(INCLUDE_DIR)/package.mk

define Package/libstk
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+lpthread +alsa-lib +lm +uclibcxx
  TITLE:=The Synthesis Toolkit in C++
  URL:=https://github.com/thestk/stk
endef

define Package/libstk/description
 This package contains a library for The Synthesis Toolkit in C++
endef

define Build/Prepare
        $(Build/Prepare/Default)
		cd $(PKG_BUILD_DIR) && autoconf
endef

LIBS:=-nodefaultlibs -lgcc -lc -luClibc++ -lm -lpthread -lasound 

define Package/libstk/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/src/libstk.a $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/src/libstk.so $(1)/usr/lib/
	$(CP) $(PKG_BUILD_DIR)/src/libstk-$(PKG_VERSION).so $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libstk))
