.. _glib:
**glib**
========
**GNOME** projesi tarafından geliştirilen, C programlama dili için temel yardımcı kütüphanedir. C programlama dilinde sıkça ihtiyaç duyulan veri yapıları, dize işlemleri, bellek yönetimi, iş parçacığı yönetimi, olay döngüsü, sinyal sistemi gibi birçok temel fonksiyonu sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="glib"
	version="2.78.0"
	description="Low-level core library that forms the basis for projects\
	 such as GTK+ and GNOME."
	source="https://download.gnome.org/sources/glib/2.78/glib-${version}.tar.xz"
	depends="bzip2,gettext,python,py3-packaging"
	builddepend="bison,flex,libffi,meson,pcre2,py3-setuptools,py3-docutils,util-linux"
	group="dev.libs"


	setup(){
	cd $SOURCEDIR
		cp $PACKAGEDIR/files/* $SOURCEDIR
		meson setup $BUILDDIR --prefix=/usr \
		    --libdir=/usr/lib64 \
		    --default-library both \
		    -D glib_debug=disabled \
		    -D selinux=disabled \
		    -D sysprof=disabled
	}

	build(){
		ninja -C $BUILDDIR
	}

	package(){
		DESTDIR=$DESTDIR ninja -C $BUILDDIR install

	}

Ek dosyaları indirmek için `tıklayınız. <https://kendilinuxunuyap.github.io/_static/files/glib/files.tar>`_


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
