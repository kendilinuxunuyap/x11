.. _xf86-video-mga:
**xf86-video-mga**
==================
Matrox grafik kartları için geliştirilmiş bir X11 video sürücüsüdür. Matrox'un MGA (Matrox Graphics Architecture) tabanlı grafik kartlarını destekler ve genellikle eski Matrox grafik donanımlarıyla uyumludur.

Matrox kartları, özellikle 3D hızlandırma ve çift monitör desteği gibi özelliklerle tanınır. Matrox'un eski grafik kartları için 2D ve bazı eski 3D grafik işlevlerini destekler.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-mga"
    version="2.0.1"
    description="Matrox video driver"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-mga/-/archive/\
    xf86-video-mga-$version/xf86-video-mga-xf86-video-mga-$version.tar.gz"
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
