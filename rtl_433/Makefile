include $(TOPDIR)/rules.mk

PKG_NAME:=rtl_433
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/merbanan/rtl_433.git
PKG_SOURCE_DATE:=2017-11-08
PKG_SOURCE_VERSION:=2d1c9459b3587ff9b4e5cc40dcc582011eb1d939
PKG_MIRROR_HASH:=9b02eeddd1461c4eef040e4cb90edbb5beb7fdc265c96975bceae6baa6e3176c

CMAKE_INSTALL:=1

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/rtl_433
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Decode data from 433 MHz transmitters
  URL:=https://github.com/merbanan/rtl_433
  DEPENDS:=+rtl-sdr
endef

define Package/rtl_433/description
  rtl_433 turns your Realtek RTL2832 based DVB dongle into a 433.92MHz generic data receiver
endef

define Package/rtl_433/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/rtl_433 $(1)/usr/bin
endef

$(eval $(call BuildPackage,rtl_433))
