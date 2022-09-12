include $(TOPDIR)/rules.mk

PKG_NAME:=omniedge
PKG_VERSION:=$$(OMNIEDGE_VERSION)
PKG_RELEASE:=$(AUTORELEASE)
PKG_ARCH:= $$(ARCH)


PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/omniedgeio/omniedge/tar.gz/$(PKG_VERSION)?
PKG_HASH:=$$(HASH256)

PKG_MAINTAINER:=omniedge <hi@omniedge.io>
PKG_LICENSE:=GPL-3.0

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/omniedgeio/omniedge-cli
GO_PKG_BUILD_PKG:=github.com/omniedgeio/omniedge-cli/out/omniedge
GO_PKG_LDFLAGS:=-s -w
GO_PKG_LDFLAGS_X:=main.Version=v$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/omniedge
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=VPN
	TITLE:=Bring intranet on the internet.
	URL:=https://github.com/omniedgeio/omniedge
	DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/omniedge/description
	Bring everything into intranet.
endef

# define Build/Compile
# 	true
# endef

# define Build/Configure
# 	true
# endef

define Package/omniedge/install
	
	$(call GoPackage/Package/Install/Bin,$(1))

	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(BUILD_DIR)/omniedge $(1)/usr/bin/omniedge

	$(INSTALL_DIR) $(1)/etc/init.d/
	$(CP) $(CURDIR)/files/omniedge.init $(1)/etc/init.d/omniedge

	$(INSTALL_DIR) $(1)/etc/
	$(CP) $(CURDIR)/files/omniedge $(1)/etc/
	
endef

$(eval $(call GoBinPackage,omniedge))
$(eval $(call BuildPackage,omniedge))
