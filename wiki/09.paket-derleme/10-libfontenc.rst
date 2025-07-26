.. _libfontenc:
**libfontenc**
==============
X11 sistemlerinde kullanılan yazı tipi kodlama bilgilerini işleyen bir kütüphanedir. Bu kütüphane genellikle bitmap fontları işlerken ve yazı tipi dönüştürmeleri yapılırken kullanılır.


.. code-block:: bash

	#!/usr/bin/env bash
	name="libfontenc"
	version="1.1.7"
	description="PX.Org fontenc library"
	source="https://www.x.org/archive/individual/lib/libfontenc-$version.tar.xz"
	depends=""
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
