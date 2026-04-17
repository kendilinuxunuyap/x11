.. _libxcb:
**libxcb**
==========
X11 için geerewkli temel kütüphanedir.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olması gerekir.

.. code-block:: bash
	
	sudo apt install xutils-dev doxygen xcb-proto_1.17.0 python3-xcbgen

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
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
