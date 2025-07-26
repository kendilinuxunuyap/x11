.. _freetype:
**freetype**
============
Açık kaynaklı bir yazı tipi motorudur. Çeşitli yazı tipi dosyalarını çözümleyip ekranda yüksek kaliteli metinlerin piksel piksel çizilmesini sağlar.


.. code-block:: bash

	#!/usr/bin/env bash
	name="freetype"
	version="2.13.1"
	description="Package freetype"
	source="https://download.savannah.gnu.org/releases/freetype/freetype-$version.tar.gz"
	depends="zlib,bzip2,glib,libpng,harfbuzz"
	group="media.libs"

	setup(){
		$SOURCEDIR/configure --prefix=/usr \
		    --libdir=/usr/lib64/ \
			--with-harfbuzz=yes
	}

	build(){
		make
	}

	package(){
		make install DESTDIR=$DESTDIR
	}


.. raw:: pdf

   PageBreak
