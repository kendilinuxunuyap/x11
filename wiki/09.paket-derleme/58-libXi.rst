.. _libXi:
**libXi**
=========
X11 (X Pencere Sistemi) için X Input Extension (Giriş Uzantısı) işlevlerini sağlayan bir kütüphanedir. X istemcilerinin klavye, fare, dokunmatik ekran gibi giriş aygıtlarına erişmesini ve bu aygıtlarla etkileşime geçmesini sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXi"
    version="1.8"
    description="X.Org Xi library"
    source="https://www.x.org/archive/individual/lib/libXi-$version.tar.gz"
    depends="libXfixes"
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
