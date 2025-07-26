.. _libpng:
**libpng**
==========
**Portable Network Graphics** (PNG) formatındaki resim dosyalarını okumak ve yazmak için kullanılan açık kaynaklı bir kütüphanedir.


.. code-block:: bash

	#!/usr/bin/env bash
	name="libpng"
	version="1.6.39"
	description="Portable Network Graphics library"
	source="https://salsa.debian.org/debian/libpng1.6/-\
	/archive/debian/$version-2/libpng1.6-debian-$version-2.tar.gz"
	depends="zlib"
	group="media.libs"


	setup(){
		cd $SOURCEDIR
		./configure --prefix=/usr \
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
