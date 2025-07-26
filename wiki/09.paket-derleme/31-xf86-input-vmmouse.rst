.. _xf86-input-vmmouse:
**xf86-input-vmmouse**
======================
Sanallaştırılmış ortamlar için geliştirilen bir giriş aygıtı sürücüsüdür. Sanal makinelerde çalışan X11 sistemlerinde fareyi doğru şekilde yönetmek için kullanılır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-input-vmmouse"
    version="13.2.0"
    description="VMWare mouse input driver"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-input-vmmouse/-/archive/\
    xf86-input-vmmouse-$version/xf86-input-vmmouse-xf86-input-vmmouse-$version.tar.gz"
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
