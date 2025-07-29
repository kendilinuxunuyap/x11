.. _libXcursor:
**libXcursor**
==============
X11 (X Pencere Sistemi) için fare imleci (cursor) yönetimini geliştiren bir kütüphanedir. Özellikle şeffaflık, ölçeklenebilirlik ve tema desteği gibi modern özellikleri sağlayarak klasik X imleç sistemini geliştirir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXcursor"
    version="1.2.1"
    description="X.Org Xcursor library"
    source="https://www.x.org/archive/individual/lib/libXcursor-$version.tar.xz"
    depends="libXrender,libXfixes,libX11"
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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
