.. _xf86-video-vesa:
**xf86-video-vesa**
===================
X11 için geliştirilmiş, genel amaçlı bir video sürücüsüdür. **VESA** (Video Electronics Standards Association) standartlarına dayanan grafik kartlarıyla çalışır ve donanım bağımsız olarak ekran çıkışı sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-vesa"
    version="2.6.0"
    description="Generic VESA video driver"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-vesa/-/archive/\
    xf86-video-vesa-$version/xf86-video-vesa-xf86-video-vesa-$version.tar.gz"
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
