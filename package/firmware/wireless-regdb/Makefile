include $(TOPDIR)/rules.mk

PKG_NAME:=wireless-regdb
PKG_RELEASE:=1
PKG_LICENSE:=ISC
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_URL:=https://git.kernel.org/pub/scm/linux/kernel/git/wens/wireless-regdb
PKG_SOURCE_PROTO:=git
PKG_SOURCE_DATE:=2025-11-05
PKG_SOURCE_VERSION:=61a463705f02b617239969c269e4882bcb5af035
PKG_MIRROR_HASH:=902d614d55c5a27c792fbefd6c5ede4c8406d01a23bf9c6214d168f818e48046

PKG_MAINTAINER:=Felix Fietkau <nbd@nbd.name>

include $(INCLUDE_DIR)/package.mk

define Package/wireless-regdb
  PKGARCH:=all
  SECTION:=firmware
  CATEGORY:=Firmware
  URL:=https://git.kernel.org/pub/scm/linux/kernel/git/wens/wireless-regdb.git/
  TITLE:=Wireless Regulatory Database
endef

define Build/Compile
	$(STAGING_DIR_HOST)/bin/$(PYTHON) $(PKG_BUILD_DIR)/db2fw.py $(PKG_BUILD_DIR)/regulatory.db $(PKG_BUILD_DIR)/db.txt
endef

define Package/wireless-regdb/install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(CP) $(PKG_BUILD_DIR)/regulatory.db $(1)/lib/firmware/
endef

$(eval $(call BuildPackage,wireless-regdb))
