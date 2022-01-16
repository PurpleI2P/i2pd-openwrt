#
# Copyright (C) 2015, 2016 gxcreator
# Copyright (C) 2017 OpenWrt.org
# Copyright (C) 2021-2022 PurpleI2P team
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=i2pd
PKG_RELEASE:=1
PKG_BUILD_PARALLEL:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/PurpleI2P/i2pd.git
PKG_SOURCE_DATE:=2022-01-16
PKG_SOURCE_VERSION:=58cf26c3049cee5f45b76361fadb65d74d32b240

PKG_MAINTAINER:=R4SAS I2P <r4sas@i2pmail.org>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/i2pd
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libopenssl +boost +boost-system +boost-filesystem \
	         +boost-program_options +boost-date_time +libatomic +zlib
	TITLE:=full-featured C++ implementation of I2P client
	URL:=https://github.com/PurpleI2P/i2pd
	USERID:=i2pd:i2pd
endef

define Package/i2pd/description
  I2P (Invisible Internet Protocol) is a universal anonymous network layer. All
  communications over I2P are anonymous and end-to-end encrypted, participants
  don't reveal their real IP addresses.
endef

TARGET_LDFLAGS+=-latomic

define Package/i2pd/conffiles
/etc/config/i2pd
/etc/i2pd/i2pd.conf
/etc/i2pd/tunnels.conf
/etc/i2pd/tunnels.d/*
endef

define Package/i2pd/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/i2pd $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/i2pd.init $(1)/etc/init.d/i2pd
	$(INSTALL_DIR) $(1)/usr/share/i2pd
	$(CP) $(PKG_BUILD_DIR)/contrib/certificates  $(1)/usr/share/i2pd
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/i2pd.config $(1)/etc/config/i2pd
	$(INSTALL_DIR) $(1)/etc/i2pd
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/contrib/i2pd.conf $(1)/etc/i2pd
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/contrib/tunnels.conf $(1)/etc/i2pd
	$(INSTALL_DIR) $(1)/etc/i2pd/tunnels.d
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/contrib/tunnels.d/README $(1)/etc/i2pd/tunnels.d
endef

$(eval $(call BuildPackage,i2pd))
