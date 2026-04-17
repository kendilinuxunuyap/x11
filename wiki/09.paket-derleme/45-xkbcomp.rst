.. _xkbcomp:
**xkbcomp**
===========
Klavye yapılandırma için kullanılan bir komut satırı aracıdır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xkbcomp"
    version="1.4.6"
    description="XKB keyboard description compiler"
    source="https://gitlab.freedesktop.org/xorg/app/xkbcomp/-/archive/\
    xkbcomp-$version/xkbcomp-xkbcomp-$version.tar.gz"
    depends="libxkbfile,libX11"
    group="x11.apps"

    setup(){
    	cd $SOURCEDIR
        autoreconf -fvi
        ./configure --prefix=/usr \
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
