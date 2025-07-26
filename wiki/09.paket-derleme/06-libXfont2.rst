.. _libXfont2:
**libXfont2**
=============
X sunucusu tarafından kullanılan bir yazı tipi erişim ve yönetim kütüphanesidir. X sunucusunun çeşitli font kaynaklarına erişmesini sağlar.


.. code-block:: bash

	#!/usr/bin/env bash
	name="libXfont2"
	version="2.0.6"
	description="X.Org Xfont library"
	source="https://www.x.org/archive/individual/lib/libXfont2-$version.tar.xz"
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
