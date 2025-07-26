.. _harfbuzz:
**harfbuzz**
============
Metin şekillendirme (text shaping) motorudur. Yazı tipi karakterlerinin, dilin ve yazım kurallarının özelliklerine göre doğru ve estetik şekilde yerleşimini sağlar.


.. code-block:: bash

	#!/usr/bin/env bash
	name="harfbuzz"
	version="8.3.0"
	description="HarfBuzz text shaping engine"
	source="https://github.com/harfbuzz/harfbuzz/archive/refs/tags/$version.tar.gz"
	depends="cairo,glib"
	group="media.libs"
	#libgirepository1.0-dev
	#libcairo2-dev
	#libchafa-dev
	setup(){
		cd $SOURCEDIR
		meson setup $BUILDDIR --prefix=/usr \
		    --libdir=/usr/lib64/ \
		    -Dglib=enabled \
			-Dgobject=enabled \
			-Dicu=enabled \
			-Dfreetype=enabled \
			-Dtests=disabled \
			-Dcairo=enabled \
			-Ddocs=enabled
	}

	build(){
		ninja -C $BUILDDIR
	}

	package(){
		DESTDIR=$DESTDIR ninja -C $BUILDDIR install
	}


.. raw:: pdf

   PageBreak
