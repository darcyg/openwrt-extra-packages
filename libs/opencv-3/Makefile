# 
# Copyright (C) 2013-2014 wrtnode.com
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=opencv3
PKG_VERSION:=3.0.0
PKG_RELEASE:=1

PKG_SOURCE:=opencv-$(PKG_VERSION).zip
PKG_SOURCE_URL:=http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$(PKG_VERSION)/
PKG_MD5SUM:=09004c275d8092cbdf5b61675cecd399

PKG_BUILD_DIR:=$(BUILD_DIR)/opencv-$(PKG_VERSION)

PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk


define Package/opencv3/Default/description
 OpenCV (Open Source Computer Vision Library) is an open source computer
 vision and machine learning software library. OpenCV was built to provide 
 a common infrastructure for computer vision applications and to accelerate 
 the use of machine perception in the commercial products. Being a 
 BSD-licensed product, OpenCV makes it easy for businesses to utilize 
 and modify the code.
endef

define Package/opencv3
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=OpenCV-3.0.0
  URL:=http://opencv.org/
  MAINTAINER:=WRTnode Team <pub@wrtnode.com>
  DEPENDS:=+libpthread +librt +libstdcpp +zlib +libjpeg +libpng +libv4l +glib2
endef


PKG_INSTALL:=1

CMAKE_OPTIONS += -DBUILD_opencv_gpu:BOOL=OFF \
	 -DWITH_1394:BOOL=OFF -DBUILD_opencv_stitching:BOOL=OFF \
	 -DBUILD_opencv_superres:BOOL=OFF -DBUILD_opencv_ts:BOOL=OFF 

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/opencv $(1)/usr/include/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/opencv2 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libopencv* $(1)/usr/lib/
endef

define Package/opencv3/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libopencv* $(1)/usr/lib/

endef

$(eval $(call BuildPackage,opencv3))

