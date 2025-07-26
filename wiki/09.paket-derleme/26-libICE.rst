.. _libICE:
**libICE**
==========
X11 pencere sistemi altında çalışan istemciler (uygulamalar) arasında protokol tabanlı iletişim kurmayı sağlayan bir kütüphanedir.

- libICE, X istemcilerinin birbirleriyle veri alışverişi yapmasını sağlar.
- ICE protokolü üzerinden bağlantı yönetimi, oturumlar arası veri paylaşımı ve kontrol sağlar.
- Genellikle libSM (Session Management) gibi üst düzey kütüphaneler tarafından kullanılır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libICE"
    version="1.1.1"
    description="X.Org Inter-Client Exchange library"
    source="https://www.x.org/archive/individual/lib/libICE-$version.tar.xz"
    depends="xorgproto"
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
