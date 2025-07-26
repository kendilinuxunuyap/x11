.. _xcalc:
**xcalc**
=========
X11 (X Pencere Sistemi) üzerinde çalışan basit bir grafiksel hesap makinesi uygulamasıdır.

**Paketi Derleme :**
--------------------

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

.. raw:: pdf

   PageBreak
