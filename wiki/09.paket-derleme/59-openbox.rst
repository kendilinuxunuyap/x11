.. _openbox:
**openbox**
===========
X11 için geliştirilmiş, hafif, esnek ve yüksek derecede özelleştirilebilir bir pencere yöneticisidir.

- openbox, yalnızca pencere yönetiminden sorumludur, yani masaüstü ortamı (desktop environment) değildir.
- Uygulamalar arasında pencere geçişi, konumlandırma, boyutlandırma ve dekorasyon işlevlerini sağlar.
- Özellikle düşük sistem kaynaklı bilgisayarlarda tercih edilir.

**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olması gerekir.

.. code-block:: bash
	
	sudo apt install libpango1.0-dev

.. code-block:: bash

    #!/usr/bin/env bash
    name="openbox"
    version="3.6.1"
    description="Highly configurable and lightweight X11 window manager"
    source="http://openbox.org/dist/openbox/openbox-$version.tar.xz"
    depends="libSM,libxml2,pango,startup-notification,libXrandr,librsvg,libXinerama"
    group="x11.wm"

    setup(){
       $SOURCEDIR/configure --prefix=/usr \
            --sysconfdir=/etc \
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
