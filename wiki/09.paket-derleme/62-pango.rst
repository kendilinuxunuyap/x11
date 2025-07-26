.. _pango:
**pango**
=========
Modern uygulamalar için tasarlanmış bir metin yerleşim ve işleme (text layout and rendering) kütüphanesidir. Özellikle çok dilli ve uluslararası metinleri doğru ve düzgün biçimde çizmek için kullanılır.

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

.. raw:: pdf

   PageBreak
