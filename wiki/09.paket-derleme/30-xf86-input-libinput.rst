.. _xf86-input-libinput:
**xf86-input-libinput**
=======================
X11 için modern giriş aygıtı sürücüsü sağlayan bir kütüphanedir. Bu sürücü, özellikle dokunmatik ekranlar, fareler, klavyeler ve çoklu dokunmatik yüzeyler gibi giriş aygıtlarını yönetir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xf86-input-libinput"
    version="1.4.0"
    description="X.org input driver based on libinput"
    source="https://gitlab.freedesktop.org/xorg/driver/xf86-input-libinput/-\/archive/\
    xf86-input-libinput-$version/xf86-input-libinput-xf86-input-libinput-$version.tar.gz"
    depends="libinput"
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
