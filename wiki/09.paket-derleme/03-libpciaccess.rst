.. _libpciaccess:
**libpciaccess**
================
PCI (Peripheral Component Interconnect) aygıtlarına erişim sağlayan düşük seviyeli bir kütüphanedir. Genellikle Linux ve Unix benzeri sistemlerde, özellikle X.Org (grafik sunucusu) projelerinde ve bazı sürücülerde kullanılır.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olası gerekir.

.. code-block:: bash

    sudo apt install build-essential autoconf automake libtool pkg-config libexpat1-dev python3

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
