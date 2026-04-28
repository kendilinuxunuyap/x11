.. _libinput:

**libinput**
============
Giriş aygıtlarını yönetmek için bir kütüphanedir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libinput"
    version="1.25.0"
    url="https://gitlab.freedesktop.org/libinput/libinput"
    description="Input device management and event handling library"
    source="https://gitlab.freedesktop.org/libinput/libinput/-/archive/\
    $version/libinput-$version.tar.gz"
    depends="eudev,mtdev,libevdev"

    setup(){
    	cd $SOURCEDIR
        meson setup $BUILDDIR --prefix=/usr \
            --libdir=/usr/lib64/ \
            -Dudev-dir=/lib64/udev \
            -Dlibwacom=true  \
            -Ddebug-gui=false \
            -Dtests=false
    }

    build(){
        ninja -C $BUILDDIR
    }

    package(){
           DESTDIR=$DESTDIR  ninja -C  $BUILDDIR install
    }


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
