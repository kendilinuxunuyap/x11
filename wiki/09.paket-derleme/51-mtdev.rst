.. _mtdev:
**mtdev**
=========
**multitouch** (çoklu dokunma) aygıtlarını yönetmek için kullanılan bir Linux kütüphanesi ve giriş aygıtı sürücüsüdür. Özellikle çoklu dokunmatik yüzeyler (multitouch touchpads, dokunmatik ekranlar vb.) ile çalışır ve çoklu dokunma olaylarını işler.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="mtdev"
    version="1.1.6"
    url="https://bitmath.org/code/mtdev/"
    description="Multitouch Protocol Translation Library"
    source="https://bitmath.org/code/mtdev/mtdev-$version.tar.gz"
    group="dev.libs"

    setup(){
        $SOURCEDIR/configure --prefix=/usr \
            --libdir=/usr/lib64/
    }

    build(){
        make $jobs
    }

    package(){
        make install DESTDIR=$DESTDIR $jobs
    }

.. raw:: pdf

   PageBreak
