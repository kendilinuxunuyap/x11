.. _libXt:
**libXt**
=========
X11 pencere sistemi için widget tabanlı GUI (grafik kullanıcı arayüzü) uygulamaları geliştirmeyi kolaylaştıran temel bir araç takımı altyapısı sağlayan bir kütüphanedir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXt"
    version="1.3.0"
    description="X.Org X Toolkit Intrinsics library"
    source="https://www.x.org/archive/individual/lib/libXt-$version.tar.gz"
    depends="libSM,libX11"
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
