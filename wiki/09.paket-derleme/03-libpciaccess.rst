.. _libpciaccess:
**libpciaccess**
================
PCI, özellikle Linux/Unix sistemlerde kullanılan; donanım aygıtlarına (özellikle X.Org ve sürücülerde) düşük seviyede erişim sağlayan bir kütüphanedir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="libpciaccess"
	version="0.17"
	description="Library providing generic access to the PCI bus and devices"
	source="https://www.x.org/archive/individual/lib/libpciaccess-$version.tar.xz"
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



**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
