.. _fontconfig:
**fontconfig**
==============
Linux ve Unix benzeri sistemlerde kullanılan, yazı tiplerini keşfetme, yapılandırma ve yönetme işlevini sağlayan bir kütüphane ve araç setidir. Sistem üzerindeki tüm yazı tiplerini tarar, organize eder ve uygulamaların kolayca kullanabilmesi için standart bir API sunar.


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


.. raw:: pdf

   PageBreak
