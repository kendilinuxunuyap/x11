.. _libxcvt:
**libxcvt**
===========
**VESA CVT** standardına uygun olarak ekran çözünürlüğü ve zamanlama bilgileri hesaplayan bir kütüphanedir. Yeni ekran çözünürlükleri oluşturmak için kullanılan hesaplama kütüphanesidir.


.. code-block:: bash

	#!/usr/bin/env bash
	name="libxcvt"
	version="0.1.2"
	description="X.Org xcvt library and cvt program"
	source="https://gitlab.freedesktop.org/xorg/lib/libxcvt/-\
	/archive/libxcvt-$version/libxcvt-libxcvt-$version.tar.gz"
	depends=""
	group="x11.libs"


	setup(){
	cd $SOURCEDIR
		meson setup $BUILDDIR --prefix=/usr \
		    --libdir=/usr/lib64/
	}

	build(){
		ninja -C $BUILDDIR
	}

	package(){
		DESTDIR=$DESTDIR ninja -C $BUILDDIR install
	}


.. raw:: pdf

   PageBreak
