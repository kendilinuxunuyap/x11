.. _libXrandr:
**libXrandr**
=============
X11 sisteminde çalışan uygulamalara, ekran çözünürlüğü ve yönü gibi ekran yapılandırmalarını dinamik olarak değiştirme yeteneği kazandıran RandR (Resize and Rotate) uzantısının istemci kütüphanesidir.

- Çözünürlük değiştirme: Monitör çözünürlüğü uygulama içinden değiştirilebilir.
- Ekran yönü: Ekran döndürme (örneğin dikey moda geçme) yapılabilir.
- Çoklu monitör desteği: Aynı anda birden fazla ekranı yapılandırabilir; konumlarını, çözünürlüklerini ve hizalamalarını değiştirebilir.
- Olay takibi: Ekran bağlantı/ayrılma olaylarını dinleyebilir (örneğin dizüstü bilgisayara ikinci ekran bağlandığında algılama).

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXrandr"
    version="1.5.3"
    description="X.Org Xrandr library"
    source="https://www.x.org/archive/individual/lib/libXrandr-$version.tar.xz"
    depends="libXrender"
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
