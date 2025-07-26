.. _libXrender:
**libXrender**
==============
X11 pencere sistemi için 2D grafiklerin daha gelişmiş ve estetik şekilde çizilmesini sağlayan bir kütüphanedir. X sunucusundaki Render (Rendere) uzantısını kullanan istemci tarafı arayüzüdür.

- X11 Render uzantısına erişim sağlar ve yarı saydamlık, alfa kanalı, yumuşatma gibi gelişmiş grafik özelliklerini destekler.
- libX11 üzerine inşa edilmiştir; onun sunduğu temel çizim işlevlerini görüntü olarak zenginleştirir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXrender"
    version="0.9.11"
    description="X.Org Xrender library"
    source="https://www.x.org/archive/individual/lib/libXrender-$version.tar.xz"
    depends=""
    group="x11.libs"

    setup(){
        $SOURCEDIR/configure --prefix=/usr \
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
