.. _libthai:
**libthai**
===========
Tayland yazı sistemini (Thai script) işlemek ve düzenlemek için kullanılan bir C kütüphanesidir. Özellikle Tayland alfabesinde yazılmış metinleri işlemek için geliştirilmiştir ve Unicode destekli metin işleme sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libthai"
    version="0.1.29"
    description="Package libthai"
    source="https://github.com/tlwg/libthai/releases/download/\
    v$version/libthai-$version.tar.xz"
    depends="libdatrie"
    group="x11.libs"

    setup(){
        $SOURCEDIR/configure --prefix=/usr \
            --libdir=/usr/lib64
    }

    build(){
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }

.. raw:: pdf

   PageBreak
