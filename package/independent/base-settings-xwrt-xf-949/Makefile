#
# Copyright (C) 2017-2019 Chen Minqiang <ptpt52@gmail.com>
# Copyright (C) 2019 X-WRT <dev@x-wrt.com>
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=base-settings-xwrt-xf-949
PKG_VERSION:=1.0.0
PKG_RELEASE:=1

PKG_MAINTAINER:=X-WRT <dev@x-wrt.com>
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk

define Package/base-settings-xwrt-xf-949/Default
  SECTION:=Applications
  CATEGORY:=Independent
  TITLE:=base-settings for xwrt_xf-949 board
  DEPENDS:=@(TARGET_ramips_mt76x8_DEVICE_xwrt_xf-949||TARGET_DEVICE_ramips_mt76x8_DEVICE_xwrt_xf-949) \
		   +libopenssl
endef

define Package/base-settings-xwrt-xf-949
  $(call Package/base-settings-xwrt-xf-949/Default)
endef

define Package/base-settings-xwrt-xf-949/description
  Standalone packages for xwrt_xf-949 board
endef

define Package/base-settings-xwrt-xf-949/conffiles
endef

define Package/base-settings-xwrt-xf-949/postinst
#!/bin/sh

if [ -z "$$IPKG_INSTROOT" ]; then
  ( . /etc/uci-defaults/96-base-settings )
  rm -f /etc/uci-defaults/96-base-settings
fi

exit 0
endef

define Package/base-settings-xwrt-xf-949/install-overlay
	$(INSTALL_DIR) $(1)/www/luci-static/openwrt2020
	$(INSTALL_DATA) ./htdocs/luci-static/openwrt2020/* $(1)/www/luci-static/openwrt2020/
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci/view/themes/openwrt2020
	$(INSTALL_DATA) ./luasrc/view/themes/openwrt2020/* $(1)/usr/lib/lua/luci/view/themes/openwrt2020/
	$(INSTALL_DATA) ./luasrc/view/sysauth.htm $(1)/usr/lib/lua/luci/view/sysauth.htm
	$(INSTALL_DATA) ./luasrc/view/factory_auth.htm $(1)/usr/lib/lua/luci/view/factory_auth.htm
	$(INSTALL_DATA) ./luasrc/view/applyreboot.htm $(1)/usr/lib/lua/luci/view/applyreboot.htm
	$(INSTALL_DIR) $(1)/www/luci-static/resources/view/status/include
	$(INSTALL_DATA) ./htdocs/luci-static/resources/view/status/include/* $(1)/www/luci-static/resources/view/status/include/
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci
	$(INSTALL_DATA) ./luasrc/dispatcher.lua $(1)/usr/lib/lua/luci/dispatcher.lua
endef

define Package/base-settings-xwrt-xf-949/install
	$(INSTALL_DIR) $(1)/etc/uci-defaults
	$(INSTALL_DATA) ./files/base-settings.defaults $(1)/etc/uci-defaults/96-base-settings
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/sncheck.bin $(1)/usr/bin/sncheck
	$(INSTALL_BIN) ./files/mt7628factory.sh $(1)/usr/bin/mt7628factory.sh
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/factory_auth.init $(1)/etc/init.d/factory_auth
endef

define Build/Configure
  true
endef

define Build/Prepare
  true
endef

define Build/Compile
  true
endef

$(eval $(call BuildPackage,base-settings-xwrt-xf-949))
