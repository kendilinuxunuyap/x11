**libunwind**
=============

Bir programın çağrı yığınını yönetmek için kullanılan bir kütüphanedir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
	name="libunwind"
	version="1.8.1"
	description="Portable and efficient API to determine the call-chain of a program"
	source="https://github.com/libunwind/libunwind/archive/refs/tags/v$version.tar.gz"
	depends=""
	builddepend="autoconf,automake,libtool"
	group="sys.libs"

	setup(){
		cd $SOURCEDIR
		autoreconf -fvi
		./configure --prefix=/usr \
		--libdir=/usr/lib64/ \
		--sysconfdir=/etc \
		--localstatedir=/var


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
