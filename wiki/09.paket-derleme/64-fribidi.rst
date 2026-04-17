.. _fribidi:
**fribidi**
===========
Unicode metinlerde metin işleme kütüphanesidir.

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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
