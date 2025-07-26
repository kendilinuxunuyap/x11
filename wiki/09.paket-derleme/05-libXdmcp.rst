.. _libXdmcp:
**libXdmcp**
============
**X Display Manager Control Protocol Library**, X11 grafik sistemi kapsamında kullanılan ve uzak X istemcileriyle oturum yönetimi yapmaya yarayan bir kütüphanedir.


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

.. raw:: pdf

   PageBreak
