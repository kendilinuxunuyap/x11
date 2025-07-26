.. _pixman:
**pixman**
==========
Pixman, grafik işlemleri için kullanılan düşük seviyeli bir kütüphanedir. Temel amacı, pikseller üzerinde doğrudan işlemler yapmaktır. 

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olası gerekir.

.. code-block:: bash

    sudo apt install build-essential autoconf automake libtool pkg-config libexpat1-dev python3

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


.. raw:: pdf

   PageBreak
