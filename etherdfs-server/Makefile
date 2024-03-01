#
# Copyright (C) 2024 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=etherdfs-server
PKG_VERSION:=20180203
PKG_RELEASE:=1

PKG_SOURCE:=ethersrv-linux-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=@SF/etherdfs
PKG_HASH:=fc6e31558367679e7e41abe143034a9996428cf482d28351adae6c6d60bf4a1a

PKG_BUILD_DIR:=$(BUILD_DIR)/ethersrv-linux-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/etherdfs-server
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=The Ethernet DOS File System
  URL:=https://etherdfs.sourceforge.net/
endef

define Package/etherdfs-server/description
	This is an EtherDFS server that exposes a network file system to
	computers running DOS and using the EtherDFS client.
endef

define Package/etherdfs-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_BUILD_DIR)/ethersrv-linux $(1)/usr/bin/$(PKG_NAME)
endef

$(eval $(call BuildPackage,etherdfs-server))
