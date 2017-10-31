include $(TOPDIR)/rules.mk

PKG_NAME:=rtl-433
PKG_VERSION:=2017-09-03
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/merbanan/rtl_433.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_DATE:=2017-09-03
PKG_SOURCE_VERSION:=c6e79a33bd443d271b8d35ccd29d32e709ff9382
# PKG_MIRROR_HASH:=79314a37709ca1ebd5fcb07b3bbcbadfad17cf5a1e7c53abba4d4be812993cc3
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
CMAKE_INSTALL:=1

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=COPYING

PKG_MAINTAINER:=Christian Lamparter <chunkeey@googlemail.com>

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/rtl-433/Default
  TITLE:=rtl-sdr based 433 MHz generic data receiver
  URL:=https://github.com/merbanan/rtl_433
endef

define Package/rtl-433/Default/description
  rtl_433 turns your Realtek RTL2832 based DVB dongle into a 433.92MHz generic data receiver
endef

define Package/rtl-433
  $(call Package/rtl-433/Default)
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libpthread +librtlsdr
endef

define Package/rtl-433/description
  $(call Package/rtl-sdr/Default/description)
endef

define Package/rtl-433/conffiles
/etc/config/rtl_433
endef

define Package/rtl-433/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/rtl_433 $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/rtl_433.init $(1)/etc/init.d/rtl_433
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_DATA) ./files/uci_rtl_433 $(1)/etc/config/rtl_433
endef

$(eval $(call BuildPackage,rtl-433))

