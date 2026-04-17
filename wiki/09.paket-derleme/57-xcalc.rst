.. _xcalc:

**xcalc**
=========

X11 üzerinde çalışan hesap makinesi uygulamasıdır.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olması gerekir.

.. code-block:: bash
	
	sudo apt install libxaw7-dev libxt-dev  libsm-dev \
	libxau-dev libxext-dev libxi-dev libxmu-dev libxt-dev

.. code-block:: bash

    #!/usr/bin/env bash
    name="xcalc"
    version="1.1.1"
    description="scientific calculator for X"
    source="https://gitlab.freedesktop.org/xorg/app/xcalc/-/archive/\
    xcalc-$version/xcalc-xcalc-$version.tar.gz"
    depends="libXaw,libICE,libSM,libXau,libXau,libXext,libXi,libXmu,libXrender,libXt,libxcb"
    group="x11.apps"

    setup(){
    	cd $SOURCEDIR
        autoreconf -fvi
        ./configure --prefix=/usr \
            --libdir=/usr/lib64/
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
