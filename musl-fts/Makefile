include $(TOPDIR)/rules.mk

PKG_NAME:=musl-fts
PKG_VERSION:=1.2.5
PKG_RELEASE:=1
PKG_LICENSE:=BSD-3-Clause

PKG_BUILD_DIR:=$(BUILD_DIR)/musl-fts-$(PKG_VERSION)
PKG_SOURCE:=v$(PKG_VERSION).tar.gz

PKG_SOURCE_URL:=https://github.com/pullmoll/musl-fts/archive/
PKG_MD5SUM:=977262d44d062778e1774158832ccb3c

PKG_BUILD_DEPENDS:=musl

# the configure script is not included in the github download
PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/autotools.mk

define Package/musl-fts
	SECTION:=lib
	CATEGORY:=Libraries
	DEFAULT:=y
	TITLE:=Implementation of fts(3) for musl libc
	URL:=https://github.com/pullmoll/musl-fts
	DEPENDS:= USE_MUSL
	MAINTAINER:=Jared Jennings <jjennings@fastmail.fm>
endef

define Package/musl-fts/description
	Implementation of fts(3) for musl libc
endef

define Build/Install
	$(call Build/Install/Default,install)
endef

define Build/InstallDev
	echo -------------------------------------------
	echo -------------------------------------------
	echo -------------------------------------------
	$(call Build/Install/Default,install DESTDIR=$(1))
	echo -------------------------------------------
	echo -------------------------------------------
	echo -------------------------------------------
endef

define Package/musl-fts/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
endef


$(eval $(call BuildPackage,musl-fts))

# -I/home/jaredj/openwrt/openwrt/build_dir/target-mips_34kc_musl-1.1.14/bro-2.4.1/src/broxygen
# -I/home/jaredj/openwrt/openwrt/build_dir/target-mips_34kc_musl-1.1.14/bro-2.4.1/src
# -I/home/jaredj/openwrt/openwrt/staging_dir/target-mips_34kc_musl-1.1.14/usr/include
# -I/home/jaredj/openwrt/openwrt/build_dir/target-mips_34kc_musl-1.1.14/bro-2.4.1/aux/binpac/lib
# -I/home/jaredj/openwrt/openwrt/staging_dir/target-mips_34kc_musl-1.1.14/include
# -I/home/jaredj/openwrt/openwrt/build_dir/target-mips_34kc_musl-1.1.14/bro-2.4.1 
