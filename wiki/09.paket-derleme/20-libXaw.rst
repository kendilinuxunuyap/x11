.. _libXaw:
**libXaw**
==========
X11 için geliştirilmiş klasik bir grafik kullanıcı arayüzü (GUI) widget kütüphanesidir. X Window System üzerinde temel GUI bileşenleri (düğmeler, listeler, menüler, metin kutuları vb.) sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="libXaw"
	version="1.0.14"
	description="Package libXaw"
	source="https://www.x.org/archive/individual/lib/libXaw-$version.tar.gz"
	depends="libXext,libXt,libXmu,libXpm"
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



**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
