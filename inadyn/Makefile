include $(TOPDIR)/rules.mk

PKG_NAME:=inadyn
PKG_VERSION:=2.13.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://github.com/troglobit/inadyn/releases/download/v$(PKG_VERSION)
PKG_HASH:=d08ca63a35896f2a809ba9b704da16ec6812b94dd410e7b3ea536a16d93860c2
PKG_MAINTAINER:=
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/inadyn/Default
  TITLE:=A Dynamic DNS client with SSL/TLS support (uses $(1))
  VARIANT=$(2)
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=IP Addresses and Names
  DEPENDS:=+confuse +ca-certificates $(3)
  URL:=https://troglobit.com/projects/inadyn/
endef

Package/inadyn-openssl=$(call Package/inadyn/Default,OpenSSL,openssl,+PACKAGE_inadyn-openssl:libopenssl)
Package/inadyn-mbedtls=$(call Package/inadyn/Default,Mbed TLS,mbedtls,+PACKAGE_inadyn-mbedtls:libmbedtls)

CONFIGURE_ARGS += \
  --$(if $(CONFIG_PACKAGE_inadyn-openssl),en,dis)able-openssl \
  --$(if $(CONFIG_PACKAGE_inadyn-mbedtls),en,dis)able-mbedtls \
  --enable-reduced \
  --enable-shared \
  --disable-static \
  --with-pic

ifneq ($(CONFIG_PACKAGE_inadyn-mbedtls),)
CONFIGURE_ARGS += \
  MbedTLS_CFLAGS="-I$(STAGING_DIR)/usr/include" \
  MbedTLS_LIBS="-lmbedtls"
endif

define Package/inadyn-$(BUILD_VARIANT)/conffiles
/etc/inadyn.conf
endef

define Package/inadyn-$(BUILD_VARIANT)/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/inadyn $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,inadyn-openssl))
$(eval $(call BuildPackage,inadyn-mbedtls))
