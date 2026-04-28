.. _xf86-video-intel:

**xf86-video-intel**
====================

Intel grafik kartları için video sürücüsüdür.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-intel"
    version="2.99.917"
    description="X.Org driver for Intel cards"
    source="https://salsa.debian.org/xorg-team/driver/xserver-xorg-video-intel/-/\
    archive/xserver-xorg-video-intel-2_$version+git20210115-1/\
    xserver-xorg-video-intel-xserver-xorg-video-intel-2_$version+git20210115-1.tar.gz"
    depends=""
    group=x11.drivers

    setup(){
    	cd $SOURCEDIR
    	./autogen.sh
        ./configure --prefix=/usr \
            --libdir=/usr/lib64/ \
            --with-default-dri=3
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
