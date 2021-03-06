#
# Copyright (C) 2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=dstat
PKG_VERSION:=0.7.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/dagwieers/dstat/archive/
PKG_MD5SUM:=be27c905e6737993306dbbcee735e8ad

include $(INCLUDE_DIR)/package.mk

define Package/dstat
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Versatile resource statistics tool
  URL:=http://dag.wieers.com/home-made/dstat/
  DEPENDS:=+python
endef

define Package/dstat/description
  Dstat is a versatile replacement for vmstat, iostat, netstat
  and ifstat. Dstat overcomes some of their limitations and
  adds some extra features, more counters and flexibility.
  Dstat is handy for monitoring systems during performance
  tuning tests, benchmarks or troubleshooting.
endef

define Build/Compile
endef

define Package/dstat/install
	$(INSTALL_DIR) $(1)/usr/share/dstat
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/dstat $(1)/usr/share/dstat/dstat.py
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/plugins/dstat_*.py $(1)/usr/share/dstat/
	$(INSTALL_DIR) $(1)/usr/bin
	$(LN) -sf ../share/dstat/dstat.py $(1)/usr/bin/dstat
endef

$(eval $(call BuildPackage,dstat))
