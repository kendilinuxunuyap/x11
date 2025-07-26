.. _openbox:
**openbox**
===========
X11 için geliştirilmiş, hafif, esnek ve yüksek derecede özelleştirilebilir bir pencere yöneticisidir.

- openbox, yalnızca pencere yönetiminden sorumludur, yani masaüstü ortamı (desktop environment) değildir.
- Uygulamalar arasında pencere geçişi, konumlandırma, boyutlandırma ve dekorasyon işlevlerini sağlar.
- Özellikle düşük sistem kaynaklı bilgisayarlarda tercih edilir.


**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="openbox"
    version="3.6.1"
    description="Highly configurable and lightweight X11 window manager"
    source="http://openbox.org/dist/openbox/openbox-$version.tar.xz"
    depends="libSM,libxml2,pango,startup-notification,libXrandr,librsvg,libXinerama"
    group="x11.wm"

    setup(){
       $SOURCEDIR/configure --prefix=/usr \
            --sysconfdir=/etc \
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
