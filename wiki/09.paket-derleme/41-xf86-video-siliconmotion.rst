.. _xf86-video-siliconmotion:
**xf86-video-siliconmotion**
============================
**Silicon Motion** grafik kartları için video sürücüsüdür.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-siliconmotion"
    version="1.7.9"
    description="Silicon Motion video driver"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-siliconmotion/-\
    /archive/xf86-video-siliconmotion-$version/\
    xf86-video-siliconmotion-xf86-video-siliconmotion-$version.tar.gz"
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
