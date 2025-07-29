.. _libXmu:
**libXmu**
==========
X11 pencere sistemi için çeşitli yardımcı işlevler sağlayan bir kütüphanedir. X uygulamaları tarafından sık kullanılan, ancak temel X kütüphanelerinde bulunmayan bazı ek fonksiyonları içerir.

X11 uygulamalarında pencere işlemleri, iletişim kutuları ve pencere özniteliklerine erişim gibi yardımcı işlevler için kullanılır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXmu"
    version="1.1.4"
    description="X.Org Xmu library"
    source="https://www.x.org/archive/individual/lib/libXmu-$version.tar.xz"
    depends="libXt,libXext,libX11"
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
