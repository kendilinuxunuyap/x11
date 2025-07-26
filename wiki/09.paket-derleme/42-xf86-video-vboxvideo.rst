.. _xf86-video-vboxvideo:
**xf86-video-vboxvideo**
========================
**VirtualBox** sanal makinesi için geliştirilmiş bir X11 video sürücüsüdür. VirtualBox üzerinde çalışan sanal makinelerde grafik hızlandırma sağlar ve sanal ekran çıkışı sunar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-video-vboxvideo"
    version="1.0.0"
    description="VirtualBox guest video driver"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-video-vbox/-/archive/\
    xf86-video-vboxvideo-$version/\
    xf86-video-vbox-xf86-video-vboxvideo-$version.tar.gz"
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
