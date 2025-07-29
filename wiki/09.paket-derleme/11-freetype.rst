.. _freetype:
**freetype**
============
Açık kaynaklı bir yazı tipi motorudur. Çeşitli yazı tipi dosyalarını çözümleyip ekranda yüksek kaliteli metinlerin piksel piksel çizilmesini sağlar.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olası gerekir.

.. code-block:: bash
	
	sudo apt install libharfbuzz-dev
	
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



**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
