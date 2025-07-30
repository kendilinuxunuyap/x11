.. _xorg-server:

**xorg-server**
===============

Linux ve Unix-benzeri sistemlerde grafik kullanıcı arayüzünün çalışmasını sağlayan bir **görüntü sunucusudur**.

"**X.Org Foundation**" tarafından geliştirilen **X Window System**'in (X11) bir parçasıdır.

Bir uygulama, X protokolü üzerinden bir pencere açmak istediğinde, bu pencereyi ekrana **xorg-server** çizer.


**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olası gerekir.

.. code-block:: bash

    sudo apt install build-essential autoconf automake libtool pkg-config \
    libexpat1-dev python3 libpixman-1-dev libxkbfile-dev libxfont-dev \
    libxcvt-dev libxext-dev libxshmfence-dev libbsd-dev libdbus-1-dev \
    libgbm-dev libepoxy-dev libaudit-dev xmlto fop \
    mesa-common-dev libgl1-mesa-dev libglx-mesa0 libxcb-util-dev \
    libxcb-shape0-dev libxcb-render0-dev libxcb-render-util0-dev \
    libxcb-image0-dev libxcb-icccm4-dev libxcb-keysyms1-dev libxcb-randr0-dev \ 
    libxcb-xkb-dev libx11-xcb-dev libxcb-xv0-dev xserver-xorg-dev libxcb-input-dev \
    libxcb-damage0-dev libxcb-sync-dev libunwind-dev libudev-dev libselinux1-dev xutils-dev
	
	# xutils-dev (xorg-macros)
    
.. code-block:: bash

	#!/usr/bin/env bash
	name="xorg-server"
	version="21.1.6"
	description="X.Org X servers"
	source="https://www.x.org/releases/individual/xserver/xorg-server-$version.tar.xz"
	depends="libmd,libbsd,libepoxy,libglvnd,libunwind,libfontenc,libxkbfile,xauth, \
	xkbcomp,setxkbmap,freetype,libXfont2,libxcvt,mesa,libX11,libdrm,pixman, \ 
	font-util,xcb-util-renderutil,xcb-util, xcb-util-image,xcb-util-wm,xcb-util-keysyms"
	group="x11.base"

	setup(){
		cd $SOURCEDIR
		meson setup $BUILDDIR --prefix=/usr \
			--libdir=/usr/lib64/ \
			-Dipv6=true -Dxvfb=true \
			-Dxnest=true -Dxcsecurity=true \
			-Dxorg=true -Dxephyr=true \
			-Dglamor=true -Dudev=true \
			-Ddtrace=false -Dsystemd_logind=false \
			-Dsuid_wrapper=true -Dxkb_dir=/usr/share/X11/xkb \
			-Dxkb_output_dir=/var/lib/xkb
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
