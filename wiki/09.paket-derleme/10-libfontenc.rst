.. _libfontenc:
**libfontenc**
==============
X11 sistemlerinde kullanılan yazı tipi kodlama bilgilerini işleyen bir kütüphanedir. Bu kütüphane genellikle bitmap fontları işlerken ve yazı tipi dönüştürmeleri yapılırken kullanılır.

**Paketi Derleme :**
--------------------

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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_



.. raw:: pdf

   PageBreak
