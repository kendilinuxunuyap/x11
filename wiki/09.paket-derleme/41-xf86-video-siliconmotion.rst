.. _xf86-video-siliconmotion:
**xf86-video-siliconmotion**
============================
**Silicon Motion** grafik kartları için geliştirilmiş bir X11 video sürücüsüdür. Silicon Motion, genellikle gömülü sistemler, taşınabilir cihazlar ve eski bilgisayarlar için grafik çözümleri üreten bir üreticidir. Silicon Motion'un SM720, SM740, SM750 gibi eski grafik kartlarıyla uyumlu çalışır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-siliconmotion"
    version="1.7.9"
    description="Silicon Motion video driver"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-siliconmotion/-\
    /archive/xf86-video-siliconmotion-$version/\
    xf86-video-siliconmotion-xf86-video-siliconmotion-$version.tar.gz"
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
