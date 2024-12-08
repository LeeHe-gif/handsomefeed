#
# Copyright (C) 2020-2021 HandsomeMod Project
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rpmsgexport
PKG_VERSION:=0.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/andersson/rpmsgexport.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=5c7299d47c1350eaf38276449f858eeef92da3e7
PKG_MIRROR_HASH:=fff8976e823eb10f6778b6bc8a405bd31c21b2186ec81b5b79f8b8cf29897dd1

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_LICENSE:=GPL-2+

include $(INCLUDE_DIR)/package.mk

define Package/rpmsgexport
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:= Create rpmsg endpoint devices for Modem
  DEPENDS:= +eudev
endef

define Package/rpmsgexport/install
	$(INSTALL_DIR) $(1)/etc/udev/rules.d
	$(INSTALL_BIN) ./files/rpmsgexport.udev $(1)/etc/udev/rules.d/55-rpmsgexport.rules

	$(INSTALL_DIR) $(1)/usr/sbin
	$(CP) $(PKG_INSTALL_DIR)/usr/local/bin/rpmsgexport $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,rpmsgexport))
