.. _xf86-input-vmmouse:

**xf86-input-vmmouse**
======================

Sanallaştırılmış ortamlarda fareyi yönetmek için kullanılır.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olması gerekir.

.. code-block:: bash
	
	sudo apt install xserver-xorg-dev

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


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
