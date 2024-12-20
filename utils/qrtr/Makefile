#
# Copyright (C) 2020-2021 HandsomeMod Project
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qrtr
PKG_VERSION:=0.3.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/LeeHe-gif/qrtr.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_VERSION:=cf851377d0296fb56990b9caffe1f0e32f824d9a
PKG_MIRROR_HASH:=2eea054cb1d11c5db498238dd00d953cbee0d39c50fd8fdd8ec6f8d3342e2d47
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
