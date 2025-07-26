.. _libxcb:
**libxcb**
==========
X11 protokolüne erişim sağlamak için geliştirilmiş, düşük seviyeli, modern ve verimli bir istemci kütüphanesidir. libX11 kütüphanesinin daha hızlı ve daha modüler bir alternatifi veya tamamlayıcısı olarak tasarlanmıştır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libxcb"
    version="1.17.0"
    description="X C-language Bindings library"
    #source="https://www.x.org/releases/individual/lib/libxcb-$version.tar.xz"
    source="https://gitlab.freedesktop.org/xorg/lib/libxcb/-\
    /archive/libxcb-$version/libxcb-libxcb-$version.tar.gz"
    depends="libXau,libXdmcp,xcb-proto"
    builddepend="libxslt,python3,util-macros"
    group="x11.libs"

    setup(){
        cd $SOURCEDIR
        #export PKG_CONFIG_PATH=/usr/lib/pkgconfig
        autoreconf -fvi
        ./configure --prefix=/usr \
        	--libdir=/usr/lib64 \
    		--enable-xinput \
    		--enable-xkb \
    		--disable-static
    }

    build(){
    	#sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }

.. raw:: pdf

   PageBreaklibxcb
