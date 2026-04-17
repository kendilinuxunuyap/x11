.. _libSM:
**libSM**
=========
X11 pencere sisteminde oturum yönetimi için gerekli kütüphanedir. 

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olması gerekir.

.. code-block:: bash
	
	sudo apt install libice-dev_1.1.1

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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
