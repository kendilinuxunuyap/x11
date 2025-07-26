.. _xf86-video-intel:
**xf86-video-intel**
====================
Intel grafik kartları için X11 video sürücüsüdür ve Intel HD Graphics ve Intel Iris Graphics gibi entegre grafik çözümleri için optimize edilmiştir. Intel'in entegre GPU'ları için X.Org Server altında yüksek performanslı 2D ve 3D grafik işleme sağlar.

Intel'in eski grafik donanımları için daha fazla uyum ve performans sağlarken, yeni Intel GPU'ları için artık yerini i915 ve mesa gibi yeni sürücülere bırakmıştır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-intel"
    version="2.99.917"
    description="X.Org driver for Intel cards"
    source="https://salsa.debian.org/xorg-team/driver/xserver-xorg-video-intel/-/\
    archive/xserver-xorg-video-intel-2_$version+git20210115-1/\
    xserver-xorg-video-intel-xserver-xorg-video-intel-2_$version+git20210115-1.tar.gz"
    depends=""
    group=x11.drivers

    setup(){
    	cd $SOURCEDIR
    	./autogen.sh
        ./configure --prefix=/usr \
            --libdir=/usr/lib64/ \
            --with-default-dri=3
    }

    build(){
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }


.. raw:: pdf

   PageBreak
