.. _xkeyboard-config:

**xkeyboard-config**
====================
X11 sistemlerinde klavye yapılandırması ve klavye seçeneklerinin yönetilmesini sağlar.

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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
