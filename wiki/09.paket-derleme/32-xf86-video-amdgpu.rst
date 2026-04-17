.. _xf86-video-amdgpu:
**xf86-video-amdgpu**
=====================
**AMD** grafik kartları için X11 video sürücüsüdür.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-amdgpu"
    version="23.0.0"
    description="Accelerated Open Source driver for AMDGPU cards"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-amdgpu/-/archive/\
    xf86-video-amdgpu-$version/xf86-video-amdgpu-xf86-video-amdgpu-$version.tar.gz"
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
