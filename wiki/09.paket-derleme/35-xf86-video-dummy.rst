.. _xf86-video-dummy:
**xf86-video-dummy**
====================
X11 için sanal (dummy) bir video sürücüsüdür. Bu sürücü, herhangi bir gerçek grafik donanımı kullanmayan, yalnızca yazılım temelli ortamlar veya test amaçları için tasarlanmıştır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-dummy"
    version="0.4.0"
    description="X.Org driver for dummy cards"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-dummy/-/archive/\
    xf86-video-dummy-$version/xf86-video-dummy-xf86-video-dummy-$version.tar.gz"
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
