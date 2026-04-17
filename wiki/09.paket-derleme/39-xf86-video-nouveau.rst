.. _xf86-video-nouveau:
**xf86-video-nouveau**
======================
NVIDIA grafik kartları için video sürücüsüdür.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="xf86-video-nouveau"
	version="1.0.17"
	description="Accelerated Open Source driver for nVidia cards"
	source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-nouveau/-/archive/\
	xf86-video-nouveau-$version/xf86-video-nouveau-xf86-video-nouveau-$version.tar.gz"
	depends=""
	group="x11.drivers"
	
	setup(){
		cp -prfv $PACKAGEDIR/files/* $SOURCEDIR/
		cd $SOURCEDIR
		patch -Np1 < ./xorg-server-21.1.diff
		autoreconf -fvi
		./configure --prefix=/usr \
		--libdir=/usr/lib64/
	}
	
	build(){
		make
	}
	
	package(){
		make install DESTDIR=$DESTDIR
	}
	
Ek dosyaları indirmek için `tıklayınız. <https://kendilinuxunuyap.github.io/_static/files/xf86-video-nouveau/files.tar>`_



**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
