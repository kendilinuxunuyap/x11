.. _xf86-video-vmware:
**xf86-video-vmware**
=====================
VMware sanal makineleri için geliştirilmiş bir X11 video sürücüsüdür. VMware sanal makinelerinde çalışan Linux ve BSD sistemlerine grafik hızlandırması ve sanal ekran yönetimi sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-vmware"
    version="13.4.0"
    description="VMware SVGA video driver"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-vmware/-/archive/\
    xf86-video-vmware-$version/xf86-video-vmware-xf86-video-vmware-$version.tar.gz"
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
