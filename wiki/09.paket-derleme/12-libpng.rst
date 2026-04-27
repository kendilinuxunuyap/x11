.. _libpng:

**libpng**
==========
**Portable Network Graphics** (PNG) formatındaki resim için kütüphanedir.

**Paketi Derleme :**
--------------------

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



**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
