.. _xf86-video-fbdev:
**xf86-video-fbdev**
====================
**framebuffer (fbdev)** tabanlı grafik kartları için X11 video sürücüsüdür. Framebuffer, ekranın bir bellek alanında (genellikle bir RAM tamponu) saklandığı bir yöntemdir, bu da daha düşük seviyede ve donanım bağımsız bir ekran çıkışı sağlar.

fbdev, düşük seviyede grafik işleme sağlar, ancak donanım hızlandırma veya 3D grafik desteği sunmaz.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-fbdev"
    version="0.5.0"
    description="video driver for framebuffer devic"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-fbdev/-/archive/\
    xf86-video-fbdev-$version/xf86-video-fbdev-xf86-video-fbdev-$version.tar.gz"
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
