.. _fribidi:
**fribidi**
===========
Tam adıyla **GNU FriBidi**, Unicode metinlerde sağdan sola (RTL - Right-To-Left) yazım desteği sağlayan bir bi-directional (bidi) metin işleme kütüphanesidir. Özellikle Arapça, İbranice, Farsça gibi sağdan sola yazılan dillerin düzgün görüntülenmesi için kullanılır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="fribidi"
    version="1.0.12"
    description="A free implementation of the unicode bidirectional algorithm"
    source="https://github.com/fribidi/fribidi/releases/download/\
    v$version/fribidi-$version.tar.xz"
    depends=""
    builddepend="meson"
    group="dev.libs"

    setup(){
        cd $SOURCEDIR
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
