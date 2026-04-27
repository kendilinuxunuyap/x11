.. _pango:
**pango**
=========

Metin işleme kütüphanesidir. 

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="pango"
    version="1.51.0"
    description="Layout and render international text"
    source="https://download.gnome.org/sources/pango/1.51/pango-$version.tar.xz"
    depends="fribidi,libthai,harfbuzz,cairo,libXft"
    makedepend="gobject-introspection"
    group="x11.libs"

    setup(){
    cd $SOURCEDIR
        meson setup $BUILDDIR --prefix=/usr \
            --libdir=/usr/lib64/ \
            -Dintrospection=enabled \
            -Dxft=enabled \
            -Dcairo=enabled \
            -Dlibthai=enabled \
            -Dfreetype=enabled \
            -Dgtk_doc=false
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
