.. _libxshmfence:
**libxshmfence**
================
X11 grafik sistemi için geliştirilmiş küçük ve özel amaçlı bir kütüphanedir. Temel görevi, paylaşılan bellek üzerinden eşzamanlama sağlamaktır.


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


.. raw:: pdf

   PageBreak
