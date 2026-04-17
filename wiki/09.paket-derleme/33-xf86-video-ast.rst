.. _xf86-video-ast:
**xf86-video-ast**
==================
**AST (Advanced Systems Technology)** grafik kartları için video sürücüsüdür.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-ast"
    version="1.1.6"
    description="X.Org driver for ASpeedTech cards"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-ast/-/archive/\
    xf86-video-ast-$version/xf86-video-ast-xf86-video-ast-$version.tar.gz"
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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
