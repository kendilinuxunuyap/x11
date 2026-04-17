.. _libffi:
**libffi**
==========
Programlama kütüphanesidir.

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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
