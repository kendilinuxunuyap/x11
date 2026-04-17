.. _libwacom:
**libwacom**
============
Dokunmatik grafik aygıtları için geliştirilmiş bir kütüphanedir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="libwacom"
	version="2.10.0"
	url="https://github.com/linuxwacom/libwacom/wiki"
	description="Library to help implement Wacom tablet settings"
	source="https://github.com/linuxwacom/libwacom/releases/download/\
	libwacom-${version}/libwacom-${version}.tar.xz"
	depends="eudev"
	builddepend="meson"
	group="dev.libs"
	setup(){
		cd $SOURCEDIR
		meson setup $BUILDDIR \
		--prefix=/usr \
		--buildtype=release \
		-Dtests=disabled
	}
	build(){
		ninja -C $BUILDDIR $jobs
	}
	
	package(){
		DESTDIR=$DESTDIR ninja -C $BUILDDIR install $jobs
		install -D -m644 COPYING "${DESTDIR}/usr/share/licenses/${name}/LICENSE"
	}


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
