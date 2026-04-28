.. _fontconfig:

**fontconfig**
==============
Sistemdeki tüm yazı tiplerini yönetimini ve kullanımını kolaylaştıran paket.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="fontconfig"
	version="2.15.0"
	description="Fontconfig is a library for configuring and customizing font access."
	source="https://www.freedesktop.org/software/fontconfig/release/fontconfig-$version.tar.gz"
	depends="freetype,expat"
	group="media.libs"


	setup(){
	cd $SOURCEDIR
		cp -prfv $PACKAGEDIR/files/* $SOURCEDIR
		meson setup $BUILDDIR --prefix=/usr \
		    --libdir=/usr/lib64/
	}

	build(){
		ninja -C $BUILDDIR
	}

	package(){
		DESTDIR=$DESTDIR ninja -C $BUILDDIR install
		# fix symlinks
		for link in $(ls ${DESTDIR}/etc/fonts/conf.d/) ; do
		    if [[ -L ${DESTDIR}/etc/fonts/conf.d/$link ]] ; then
		    rm -f ${DESTDIR}/etc/fonts/conf.d/$link
		    ln -s ../../../usr/share/fontconfig/conf.avail/$link ${DESTDIR}/etc/fonts/conf.d/$link
		    fi
		done

	}



**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
