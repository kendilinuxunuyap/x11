.. _libXext:
**libXext**
===========
X sunucusundaki ek özelliklerin (uzantıların) istemciler tarafından kolayca kullanılmasını sağlayan bir kütüphanedir.


.. code-block:: bash

	#!/usr/bin/env bash
	name="libXext"
	version="1.3.5"
	description="X.Org Xext library"
	source="https://www.x.org/archive/individual/lib/libXext-$version.tar.xz"
	depends="libX11,xorgproto"
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
