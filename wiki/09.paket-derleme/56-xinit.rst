.. _xinit:
**xinit**
=========
X Pencere Sistemi (X11) için kullanılan bir başlatıcı komuttur. X sunucusunu başlatmak ve onunla birlikte bir istemci (örneğin bir pencere yöneticisi veya masaüstü ortamı) çalıştırmak için kullanılır.

xinit, doğrudan X sunucusunu başlatır ve ardından kullanıcı tarafından belirtilen bir istemci programı çalıştırır (örneğin: xterm, startkde, startxfce4, vs.).

Genellikle grafik arayüzü olmayan sistemlerde veya özel oturumlarda kullanılır.

~/.xinitrc dosyası aracılığıyla hangi istemcilerin çalıştırılacağı belirlenebilir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

	#!/usr/bin/env bash
	name="xinit"
	version="1.4.2"
	description="X Window System initializer xinit"
	source="https://gitlab.freedesktop.org/xorg/app/xinit/-/archive/\
	xinit-$version/xinit-xinit-1.4.2.tar.gz"
	depends="util-macros,xorgproto,libX11,xorg-server,xterm,xhost,xrdb"
	group="x11.apps"


	setup(){
		cp -prfv ${dizin}/${paket}/files /tmp/bps/build/files/
		cp -prfv $PACKAGEDIR/files $SOURCEDIR
		cd $SOURCEDIR
		
		autoreconf -vfi
		./configure --prefix=/usr \
		    --libdir=/usr/lib64/ \
		    -sysconfdir=/etc
	}

	build(){
		make
	}

	package(){
		make install DESTDIR=$DESTDIR
		install -m755 -D $SOURCEDIR/files/Xwrapper.config "$DESTDIR"/etc/X11/Xwrapper.config
		install -m755 -D $SOURCEDIR/files/xinitrc "$DESTDIR"/etc/X11/xinit/xinitrc
		install -m755 -D $SOURCEDIR/files/Xsession "$DESTDIR"/etc/X11/xinit/Xsession
		install -m755 $SOURCEDIR/files/xserverrc "$DESTDIR"/etc/X11/xinit/xserverrc
		install -m755 -D $SOURCEDIR/files/xinit.sysconf "$DESTDIR"/etc/sysconf.d/xinit
		install -m755 -D $SOURCEDIR/files/xinit.initd "$DESTDIR"/etc/init.d/xinit
		install -m755 -D $SOURCEDIR/files/xinit.confd "$DESTDIR"/etc/conf.d/xinit
		install $SOURCEDIR/files/Xresources "$DESTDIR"/etc/X11/Xresources
		# allow local connections config
		mkdir -p "$DESTDIR"/etc/X11/xinit/xinitrc.d
		echo "#!/bin/sh" > "$DESTDIR"/etc/X11/xinit/xinitrc.d/10-local.sh
		echo "xhost +local:" >> "$DESTDIR"/etc/X11/xinit/xinitrc.d/10-local.sh
		chmod 754 "$DESTDIR"/etc/X11/xinit/xinitrc.d/10-local.sh
	}

Ek dosyaları indirmek için `tıklayınız. <https://kendilinuxunuyap.github.io/_static/files/xinit/files.tar>`_

.. raw:: pdf

   PageBreak
