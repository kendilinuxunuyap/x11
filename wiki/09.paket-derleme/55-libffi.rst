.. _libffi:
**libffi**
==========
C programlarının başka dillerde yazılmış (örneğin Python, Ruby, Lua gibi) fonksiyonları çalışma zamanında çağırabilmesini sağlayan bir düşük seviyeli programlama kütüphanesidir. Adı "foreign function interface" yani "yabancı fonksiyon arayüzü" anlamına gelir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/bin/bash
    name="libffi"
    version="3.4.6"
    description="A portable foreign-function interface library. "
    source="https://github.com/libffi/libffi/releases/download/v${version}/\
    libffi-${version}.tar.gz"
    depends=""
    builddepend=""
    group="dev.libs"

    setup(){
    	cd $SOURCEDIR
        ./configure --prefix=/usr \
            --libdir=/usr/lib64/ \
            --enable-pax_emutramp \
    		--enable-portable-binary \
    		--disable-exec-static-tramp
    }

    build(){
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }

.. raw:: pdf

   PageBreak
