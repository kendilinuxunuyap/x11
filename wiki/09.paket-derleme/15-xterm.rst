.. _xterm:
**xterm**
=========
Unix ve Linux sistemlerde kullanılan klasik, sade ve hafif bir terminal emülatörüdür.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olması gerekir.

.. code-block:: bash
	
	sudo apt install  libxt-dev libxinerama-dev libxaw7-dev
	
.. code-block:: bash


	#!/usr/bin/env bash
	name="xterm"
	version="388"
	description="Terminal Emulator for X Windows"
	depends="libX11,ncurses,util-linux,libXt,libXau,libXinerama,libXaw,libXpm,libXft"
	source="https://invisible-island.net/archives/xterm/xterm-$version.tgz"
	group="x11.terms"


	setup(){
		cp -prfv $PACKAGEDIR/files/* $SOURCEDIR

		$SOURCEDIR/configure --prefix=/usr --libdir=/usr/lib64/ --exec-prefix=/usr \
			--with-app-defaults=/etc/X11/app-defaults --with-icondir=/usr/share/icons \
			--with-icon-theme=yes --with-tty-group=tty --enable-warnings --enable-logging \
			--enable-wide-chars --enable-luit --enable-256-color --disable-imake \
			--enable-narrowproto --enable-exec-xterm --enable-dabbrev --enable-backarrow-is-erase \
			--enable-sixel-graphics --with-utempter --with-desktop-category=System,TerminalEmulator
	}

	build(){
		make
	}

	package(){
		make install DESTDIR=$DESTDIR
		make install-ti $jobs DESTDIR=${DESTDIR}
		mkdir -p "${DESTDIR}"/usr/share/applications
		mkdir -p "${DESTDIR}"/usr/share/xgreeters
		install $SOURCEDIR/{xterm,uxterm}.desktop "${DESTDIR}"/usr/share/applications/
		install $SOURCEDIR/xterm.desktop "${DESTDIR}"/usr/share/xgreeters/
	}
	
Ek dosyaları indirmek için `tıklayınız. <https://kendilinuxunuyap.github.io/_static/files/xterm/files.tar>`_


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
