.. _dejavu:
**dejavu**
==========
Açık kaynaklı ve geniş kapsamlı bir yazı tipi ailesidir. Çok sayıda dil ve karakter setini kapsayan, özgür ve kaliteli fontlar sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="dejavu"
	version="2.37"
	description="DejaVu fonts, bitstream vera with ISO-8859-2 characters"
	source="https://github.com/dejavu-fonts/dejavu-fonts/releases/download/\
	version_${version/./_}/dejavu-lgc-fonts-ttf-$version.zip"
	depends=""
	group="media.fonts"
	setup()
	{
		/bin/busybox wget "https://github.com/dejavu-fonts/dejavu-fonts/releases/\
		download/version_${version/./_}/dejavu-fonts-ttf-$version.zip"
		
		/bin/busybox unzip dejavu-fonts-ttf-$version.zip
		/bin/busybox rm dejavu-fonts-ttf-$version.zip
		/bin/busybox cp -prfv $SOURCEDIR ./  
	}
	build()
	{
	echo ""
	}
	package(){
		mkdir -p ${DESTDIR}/usr/share/fonts
		for font in dejavu dejavu-fonts-ttf; do
		    cp -prfv $BUILDDIR/$font-$version/ttf ${DESTDIR}/usr/share/fonts/$font
		done
	}



**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
