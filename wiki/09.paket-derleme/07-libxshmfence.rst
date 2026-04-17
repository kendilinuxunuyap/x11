.. _libxshmfence:
**libxshmfence**
================
X11 için geliştirilmiş, paylaşılan bellek üzerinden eşzamanlama sağlayan küçük ve özel amaçlı bir kütüphanedir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="libxshmfence"
	version="1.3.2"
	description="Shared memory fences using futexes"
	source="https://www.x.org/archive/individual/lib/libxshmfence-$version.tar.xz"
	depends="xorgproto"
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
