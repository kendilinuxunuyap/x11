.. _libSM:
**libSM**
=========
X11 pencere sisteminde oturum yönetimi (session management) işlevlerini sağlayan bir kütüphanedir. Uygulamaların, oturum kapanmadan önce kayıt yapmasını, sonraki oturumda kaldığı yerden devam etmesini mümkün kılar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libSM"
    version="1.2.4"
    description="libSM X.Org Session Management library"
    source="https://www.x.org/archive/individual/lib/libSM-$version.tar.xz"
    depends="xorgproto,libICE"
    group="x11.libs"

    setup(){
        $SOURCEDIR/configure --prefix=/usr \
            --libdir=/usr/lib64
    }

    build(){
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }

.. raw:: pdf

   PageBreak
