.. _xf86-video-ast:
**xf86-video-ast**
==================
**AST (Advanced Systems Technology)** grafik kartları için geliştirilmiş bir X11 video sürücüsüdür. AST kartları genellikle gömülü sistemler, iş istasyonları ve sunucu uygulamaları gibi alanlarda kullanılır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-ast"
    version="1.1.6"
    description="X.Org driver for ASpeedTech cards"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-ast/-/archive/\
    xf86-video-ast-$version/xf86-video-ast-xf86-video-ast-$version.tar.gz"
    depends=""
    group="x11.drivers"

    setup(){
    	cd $SOURCEDIR
    	./autogen.sh
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
