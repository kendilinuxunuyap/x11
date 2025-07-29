.. _harfbuzz:
**harfbuzz**
============
Metin şekillendirme (text shaping) motorudur. Yazı tipi karakterlerinin, dilin ve yazım kurallarının özelliklerine göre doğru ve estetik şekilde yerleşimini sağlar.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olası gerekir.

.. code-block:: bash
	
	sudo apt install libcairo2-dev gtk-doc-tools

.. code-block:: bash

	#!/usr/bin/env bash
	name="harfbuzz"
	version="8.3.0"
	description="HarfBuzz text shaping engine"
	source="https://github.com/harfbuzz/harfbuzz/archive/refs/tags/$version.tar.gz"
	depends="cairo,glib"
	group="media.libs"
	#libgirepository1.0-dev
	#libcairo2-dev
	#libchafa-dev
	setup(){
		cd $SOURCEDIR
		meson setup $BUILDDIR --prefix=/usr \
		    --libdir=/usr/lib64/ \
		    -Dglib=enabled \
			-Dgobject=enabled \
			-Dicu=enabled \
			-Dfreetype=enabled \
			-Dtests=disabled \
			-Dcairo=enabled \
			-Ddocs=enabled
	}

	build(){
		ninja -C $BUILDDIR
	}

	package(){
		DESTDIR=$DESTDIR ninja -C $BUILDDIR install
	}


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_



.. raw:: pdf

   PageBreak
