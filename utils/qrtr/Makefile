#
# Copyright (C) 2020-2021 HandsomeMod Project
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qrtr
PKG_VERSION:=0.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/scintill/qrtr.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=eb5ee83dee85f7fc086016c949b6bf7f6b6a3288
PKG_MIRROR_HASH:=2234f69eeb7707dd174afd4196eb154a5f25b81109263dd1ba97d5a21d9ae43e

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_LICENSE:=GPL-2+

include $(INCLUDE_DIR)/package.mk

define Package/libqrtr
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Userspace reference for net/qrtr in the Linux kernel
endef

define Package/qrtr-ns
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libqrtr
  TITLE:=qrtr daemon
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/libqrtr.h \
		$(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libqrtr.so* \
		$(1)/usr/lib/
endef


define Package/libqrtr/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libqrtr.so* $(1)/usr/lib/
endef

define Package/qrtr-ns/install
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/qrtr.init $(1)/etc/init.d/qrtr

	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/qrtr-ns $(1)/usr/bin/
endef

$(eval $(call BuildPackage,libqrtr))
$(eval $(call BuildPackage,qrtr-ns))
