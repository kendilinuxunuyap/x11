.. _xkeyboard-config:
**xkeyboard-config**
====================
X11 sistemlerinde klavye düzenlerini (layout) ve klavye seçeneklerini yapılandırmak için kullanılan bir konfigürasyon dosyası paketidir. Bu paket, X Keyboard Extension (XKB) kullanarak, farklı klavye düzenlerinin, tuş atamalarının ve klavye seçeneklerinin yönetilmesini sağlar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xkeyboard-config"
    version="2.40"
    description="X keyboard configuration database"
    source="https://gitlab.freedesktop.org/xkeyboard-config/xkeyboard-config/-/\
    archive/xkeyboard-config-$version/xkeyboard-config-xkeyboard-config-$version.tar.gz"
    depends=""
    group="x11.misc"

    setup(){
    	cd $SOURCEDIR
        meson setup $BUILDDIR --prefix=/usr \
            --libdir=/usr/lib64/
    }

    build(){
        ninja -C $BUILDDIR
    }

    package(){
        DESTDIR=$DESTDIR ninja -C $BUILDDIR install
    }

.. raw:: pdf

   PageBreak
