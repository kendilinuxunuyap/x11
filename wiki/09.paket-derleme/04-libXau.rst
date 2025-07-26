.. _libXau:
**libXau**
==========
X11 (X Window System) ile birlikte kullanılan bir yetkilendirme (authentication) kütüphanesidir. X istemcileri ile X sunucusu  arasında bağlantı kurulurken güvenlik doğrulaması sağlar.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olası gerekir.

.. code-block:: bash

    sudo apt install build-essential autoconf automake libtool pkg-config libexpat1-dev python3

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


.. raw:: pdf

   PageBreak
