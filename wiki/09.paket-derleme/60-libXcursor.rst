.. _libXcursor:
**libXcursor**
==============
X11 (X Pencere Sistemi) için fare imleci (cursor) yönetimini geliştiren bir kütüphanedir. Özellikle şeffaflık, ölçeklenebilirlik ve tema desteği gibi modern özellikleri sağlayarak klasik X imleç sistemini geliştirir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXcursor"
    version="1.2.1"
    description="X.Org Xcursor library"
    source="https://www.x.org/archive/individual/lib/libXcursor-$version.tar.xz"
    depends="libXrender,libXfixes,libX11"
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
