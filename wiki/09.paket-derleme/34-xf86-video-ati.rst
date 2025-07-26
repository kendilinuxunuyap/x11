.. _xf86-video-ati:
**xf86-video-ati**
==================
AMD/ATI grafik kartları için X11 video sürücüsüdür. Bu sürücü, eski ATI Radeon grafik kartları için temel 2D grafik hızlandırması sağlar ve X.Org Server'da çalışır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="xf86-video-ati"
	version="22.0.0"
	description="ATI video driver"
	source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-ati/-/archive/\
	xf86-video-ati-$version/xf86-video-ati-xf86-video-ati-$version.tar.gz"
	depends=""
	group="x11.drivers"

	setup(){
		cp -prfv $PACKAGEDIR/files/* $SOURCEDIR
		cd $SOURCEDIR
		patch -Np1 -i $SOURCEDIR/patches/xf86-video-ati-19.1.0-upstream_fixes-1.patch
		./autogen.sh
		./configure --prefix=/usr \
		    --libdir=/usr/lib64/
	}

	build(){
		make
	}

	package(){
		make install DESTDIR=$DESTDIR
	}
	
Ek dosyaları indirmek için `tıklayınız. <https://kendilinuxunuyap.github.io/_static/files/xf86-video-ati/files.tar>`_

.. raw:: pdf

   PageBreak
