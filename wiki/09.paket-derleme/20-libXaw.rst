.. _libXaw:
**libXaw**
==========
X11 için geliştirilmiş klasik bir grafik kullanıcı arayüzü (GUI) widget kütüphanesidir. X Window System üzerinde temel GUI bileşenleri (düğmeler, listeler, menüler, metin kutuları vb.) sağlar.


.. code-block:: bash

	#!/usr/bin/env bash
	name="libXaw"
	version="1.0.14"
	description="Package libXaw"
	source="https://www.x.org/archive/individual/lib/libXaw-$version.tar.gz"
	depends="libXext,libXt,libXmu,libXpm"
	group="x11.libs"


	setup(){
		$SOURCEDIR/configure --prefix=/usr \
		    --libdir=/usr/lib64/
	}

	build(){
		make
	}

	package(){
		make install DESTDIR=$DESTDIR
	}


.. raw:: pdf

   PageBreak
