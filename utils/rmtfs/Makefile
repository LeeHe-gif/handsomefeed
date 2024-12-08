#
# Copyright (C) 2020-2021 HandsomeMod Project
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=rmtfs
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/andersson/rmtfs.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=695d0668ffa6e2a4bf6e676f3c58a444a5d67690
PKG_MIRROR_HASH:=7ddadf30b9281ed4b041faaf77fcea2b8f4bf8227487e940b8f98454e69a7907

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_LICENSE:=GPL-2+

include $(INCLUDE_DIR)/package.mk

define Package/rmtfs
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Qualcomm Remote Filesystem Service Implementation
  DEPENDS:=+eudev +libqrtr +qrtr-ns
endef

define Package/rmtfs/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/rmtfs.init $(1)/etc/init.d/rmtfs

	$(INSTALL_DIR) $(1)/etc/udev/rules.d
	$(INSTALL_BIN) ./files/rmtfs.udev $(1)/etc/udev/rules.d/65-rmtfs.rules

	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/local/bin/rmtfs $(1)/usr/bin/
endef

$(eval $(call BuildPackage,rmtfs))
