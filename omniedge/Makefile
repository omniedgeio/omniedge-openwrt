include $(TOPDIR)/rules.mk

PKG_NAME:=omniedge
OMNIEDGE_VERSION?=1.0.2-beta.0
PKG_VERSION:=$(OMNIEDGE_VERSION)
PKG_RELEASE:=$(AUTORELEASE)
OMNIEDGE_ARCH?=$(ARCH)
PKG_SOURCE:=$(PKG_NAME)-v$(PKG_VERSION)-openwrt-$(OMNIEDGE_ARCH).zip
PKG_SOURCE_URL:=https://github.com/omniedgeio/omniedge/releases/download/v$(PKG_VERSION)
PKG_HASH:=$(HASH256)
PKG_MAINTAINER:=omniedge <hi@omniedge.io>
PKG_LICENSE:=GPL-3.0

include $(INCLUDE_DIR)/package.mk

define Package/omniedge
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+ca-bundle +kmod-tun
	SUBMENU:=VPN
	TITLE:=Bring intranet on the internet.
	URL:=https://github.com/omniedgeio/omniedge
endef

define Package/omniedge/description
	Bring everything into intranet.
endef

define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
	$(UNZIP) -j -d $(PKG_BUILD_DIR) $(DL_DIR)/$(PKG_SOURCE)
	find $(PKG_BUILD_DIR) -type f -name "omniedge*" -not -name "omniedge" -exec mv {} $(PKG_BUILD_DIR)/omniedge \;
endef

define Build/Compile
	true
endef

define Build/Configure
	true
endef

define Package/omniedge/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_BUILD_DIR)/omniedge $(1)/usr/bin/omniedge

	$(INSTALL_DIR) $(1)/etc/init.d/
	$(CP) $(CURDIR)/files/omniedge.init $(1)/etc/init.d/omniedge

	$(INSTALL_DIR) $(1)/etc/
	$(CP) $(CURDIR)/files/omniedge $(1)/etc/
	
endef

$(eval $(call BuildPackage,omniedge))
