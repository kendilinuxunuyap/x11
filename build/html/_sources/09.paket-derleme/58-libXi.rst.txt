.. _libXi:

**libXi**
=========
X uygulamarında giriş aygıtlarına erişmesini sağlar.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olması gerekir.

.. code-block:: bash
	
	sudo apt install libxfixes-dev

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXi"
    version="1.8"
    description="X.Org Xi library"
    source="https://www.x.org/archive/individual/lib/libXi-$version.tar.gz"
    depends="libXfixes"
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
