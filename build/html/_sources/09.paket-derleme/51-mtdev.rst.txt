.. _mtdev:

**mtdev**
=========

**multitouch** (çoklu dokunma) aygıtlarını için sürücüdür.

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
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_

.. raw:: pdf

   PageBreak
