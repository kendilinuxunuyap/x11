.. _xcb-util:
**xcb-util**
============
X11 için geliştirilmiş bir genel yardımcı araçlar kütüphanesidir ve XCB (X C Binding) API'si ile uyumlu çalışan çeşitli araçlar sunar. xcb-util kütüphanesi, X11 uygulamalarının daha esnek ve fonksiyonel olmasını sağlayan birçok küçük ama önemli işlevi içerir.

- Yüksek seviyeli X11 işlevleri: xcb-util, libxcb'nin sunduğu temel işlevlikten daha yüksek seviyede işlevler sağlar.
- Pencere yöneticisi eklentileri: Örneğin, pencere yöneticileri için kullanılan bazı ekstra özellikler (xprop gibi) sağlar.
- X11 protokolü genişletme: X11 sunucusunun bazı protokollerine daha kolay erişim sağlayan işlevler sunar.
- Daha hızlı XCB kullanımı: XCB'nin daha düşük seviyeli işlevlerini daha hızlı ve kolay bir şekilde kullanma olanağı tanır.


**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="xcb-util"
    version="0.4.0"
    description="X C-language Bindings sample implementations"
    source="https://www.x.org/releases/individual/xcb/xcb-util-${version}.tar.gz"
    depends="libxcb,util-macros,xorgproto"
    group="x11.libs"

    setup(){
    	$SOURCEDIR/configure --prefix=/usr \
    		--libdir=/usr/lib64 \
    		--enable-shared \
    		--enable-static \
    		--disable-devel-docs \
    		--without-doxygen
    }

    build(){
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }

.. raw:: pdf

   PageBreak
