.. _pixman:
**pixman**
==========
Pixman, grafik işlemleri için kullanılan düşük seviyeli bir kütüphanedir. Temel amacı, pikseller üzerinde doğrudan işlemler yapmaktır. 

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="pixman"
	version="0.42.2"
	description="Low-level pixel manipulation routines"
	source="https://www.x.org/archive/individual/lib/pixman-$version.tar.gz"
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
