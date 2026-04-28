.. _libdrm:

**libdrm**
==========
Linux’ta grafik donanımına güvenli ve doğrudan erişim imkânı sunan bir ara kütüphanedir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="libdrm"
	version="2.4.120"
	description="X.Org libdrm library"
	source="https://dri.freedesktop.org/libdrm/libdrm-$version.tar.xz"
	depends="libpciaccess"
	group="x11.libs"


	setup(){
		cd $SOURCEDIR
		meson setup $BUILDDIR --prefix=/usr \
			-D default_library=both \
			-D udev=false \
			-D etnaviv=disabled \
			-D freedreno=disabled \
			-D vc4=disabled \
			-D valgrind=disabled \
			-D install-test-programs=true
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
