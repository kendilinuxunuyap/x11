.. _xf86-video-amdgpu:
**xf86-video-amdgpu**
=====================
**AMD** grafik kartları için X11 video sürücüsüdür ve **AMD Radeon** ve **AMD Vega** serisi grafik kartlarıyla uyumlu çalışır. Bu sürücü, **amdgpu** adlı açık kaynaklı AMD GPU sürücüsünü kullanarak, X.Org Server'da donanım hızlandırması ve yüksek performanslı grafik işlevi sağlar.

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

.. raw:: pdf

   PageBreak
