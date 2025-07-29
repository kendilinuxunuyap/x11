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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
