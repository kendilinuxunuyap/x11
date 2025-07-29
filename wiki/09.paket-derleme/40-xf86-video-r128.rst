.. _xf86-video-r128:
**xf86-video-r128**
===================
ATI R128 serisi grafik kartları için geliştirilmiş bir X11 video sürücüsüdür. Bu sürücü, ATI R128 (Rage 128) tabanlı grafik kartları için 2D grafik hızlandırma ve ekran yönetimi sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-r128"
    version="6.12.1"
    description="ATI Rage128 video drive"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-r128/-/archive/\
    xf86-video-r128-$version/xf86-video-r128-xf86-video-r128-$version.tar.gz"
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
