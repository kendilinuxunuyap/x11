.. _libXft:
**libXft**
==========
X11 grafik sisteminde FreeType yazı tipi motorunu kullanarak daha güzel, pürüzsüz (antialiased) metinler göstermek için kullanılan bir kütüphanedir.

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXft"
    version="2.3.7"
    description="XFreeType-based font drawing library for X"
    source="https://www.x.org/archive/individual/lib/libXft-$version.tar.xz"
    depends="fontconfig,libXrender"
    group="x11.libs"
    
    
    setup(){
        $SOURCEDIR/configure --prefix=/usr \
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
