.. _libXau:
**libXau**
==========
X11 ile kullanılan, istemci ile sunucu arasındaki bağlantıda kimlik doğrulaması yapan bir yetkilendirme kütüphanesidir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="libXau"
	version="1.0.11"
	description="X.Org X authorization library"
	source="https://www.x.org/releases/individual/lib/libXau-${version}.tar.xz"
	depends="xorgproto"
	builddepend=""
	group="x11.libs"


	setup(){
		export PKG_CONFIG_PATH=/usr/lib/pkgconfig
		cd $SOURCEDIR
		./configure --prefix=/usr \
			--sysconfdir=/etc \
			--without-xproto
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
