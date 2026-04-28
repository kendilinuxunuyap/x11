.. _libXdmcp:

**libXdmcp**
============
X11 kapsamında, uzak istemcilerle oturum yönetimini sağlayan bir kütüphanedir


**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="libXdmcp"
	version="1.1.5"
	description="X.Org X Display Manager Control Protocol library"
	source="https://www.x.org/archive/individual/lib/libXdmcp-$version.tar.xz"
	depends=""
	builddepend="xorgproto util-macros xmlto"
	group="x11.libs"


	setup(){
		cd $SOURCEDIR
		export PKG_CONFIG_PATH=/usr/lib/pkgconfig
		./configure --prefix=/usr \
			--sysconfdir=/etc
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
