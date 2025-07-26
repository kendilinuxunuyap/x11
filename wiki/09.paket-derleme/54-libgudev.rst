.. _libgudev:
**libgudev**
============
Linux tabanlı sistemlerde donanım aygıtlarını yönetmek için kullanılan bir C kütüphanesidir. udev (Linux'un cihaz yöneticisi) ile uyumlu çalışarak, sistemdeki donanım aygıtları ile etkileşimi kolaylaştırır. libgudev, özellikle donanım aygıtlarının tanınması, bağlantı ve bağlantı olaylarının izlenmesi gibi işlevleri yönetir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libgudev"
    version="238"
    url="https://example.org"
    description="GObject bindings for libudev"
    source="https://gitlab.gnome.org/GNOME/libgudev/-/archive/$version/\
    libgudev-$version.tar.gz"
    depends="glib,eudev"
    builddepend=""
    group="dev.libs"

    setup(){
    cd $SOURCEDIR
        meson setup $BUILDDIR --prefix=/usr \
            --libdir=/usr/lib64/ \
            -Dintrospection=enabled \
    		-Dvapi=enabled \
    		-Dgtk_doc=false
    }

    build(){
        meson compile -C $BUILDDIR
    }

    package(){
        DESTDIR="$DESTDIR" meson install -C $BUILDDIR
    }

.. raw:: pdf

   PageBreak
