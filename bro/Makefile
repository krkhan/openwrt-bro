include $(TOPDIR)/rules.mk

PKG_NAME:=bro
PKG_VERSION:=2.4.1
PKG_RELEASE:=2

PKG_BUILD_DIR:=$(BUILD_DIR)/bro-$(PKG_VERSION)
PKG_SOURCE:=bro-$(PKG_VERSION).tar.gz

PKG_SOURCE_URL:=http://www.bro-ids.org/downloads/release/
PKG_MD5SUM:=353e79df458e2bbfa00bdbaa0f183908

PKG_CAT:=zcat
PKG_INSTALL:=1

PKG_BUILD_DEPENDS:=bro/host
HOST_BUILD_DEPENDS:=libpcap/host file/host zlib/host openssl/host bind/host
HOST_BUILD_DIR:=$(BUILD_DIR_HOST)/bro-$(PKG_VERSION)

include $(INCLUDE_DIR)/host-build.mk

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += -DBIND_INCLUDE_DIR=$(STAGING_DIR)/include \
	-DBIFCL_HOST:PATH=$(HOST_BUILD_DIR)/src/bifcl \
	-DBINPAC_HOST:PATH=$(HOST_BUILD_DIR)/aux/binpac/src/binpac \
	-DINSTALL_BROCCOLI=false \
	-DDISABLE_PERFTOOLS=true \
	-DDISABLE_PYTHON_BINDINGS=true \
	-DDISABLE_RUBY_BINDINGS=true \
	-DDISABLE_DATASERIES=true \
	-DDISABLE_ELASTICSEARCH=true \
	-DBINARY_PACKAGING_MODE:BOOL=true

HOST_CONFIGURE_ARGS :=
HOST_CONFIGURE_VARS := --prefix=$(STAGING_DIR_HOST)/bro

define Package/bro
	SECTION:=net
	CATEGORY:=Network
	DEFAULT:=y
	TITLE:=Network security Monitor
	URL:=http://www.bro-ids.org/
	DEPENDS:= +libopenssl +libpcap +libmagic \
		+libncurses +libstdcpp +zlib +bind-libs
endef

define Package/bro/description
	Network security monitor.
endef

define Package/bro/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/bin/bro \
		$(1)/usr/bin/
	$(RSTRIP) \
		$(1)/usr/bin/bro
	mkdir -p $(1)/usr/share/bro
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/share/bro/* \
		$(1)/usr/share/bro/
	mkdir -p $(1)/usr/lib
endef

$(eval $(call HostBuild,bro))
$(eval $(call BuildPackage,bro))
