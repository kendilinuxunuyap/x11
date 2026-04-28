.. _libglvnd:

**libglvnd**
============
OpenGL (GL), grafik sürücü yönetimini için kütüphanedir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libglvnd"
    version="1.7.0"
    description="The GL Vendor-Neutral Dispatch library"
    source="https://gitlab.freedesktop.org/glvnd/libglvnd/-/archive/\
    v$version/libglvnd-v$version.tar.gz"
    depends="libXext"
    group="media.libs"

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
