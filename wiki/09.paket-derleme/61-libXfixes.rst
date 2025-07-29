.. _libXfixes:
**libXfixes**
=============
X11 (X Pencere Sistemi) için geliştirilen Xfixes uzantısının (X Fixes Extension) istemci tarafı kütüphanesidir. Bu uzantı, X11 protokolüne çeşitli küçük ama önemli iyileştirmeler getirir ve bu iyileştirmeleri uygulamaların kullanabilmesini sağlar.

**Sağladığı Başlıca Özellikler:**
---------------------------------

- İmleç gizleme ve değiştirme: Uygulamalar imleci gizleyebilir veya özel bir görünümle değiştirebilir.
- Bölge yönetimi (Region handling): Ekranın sadece belirli bölgelerinde yeniden çizim yapılmasını sağlar (örneğin pencere efektleri için).
- Selection notifikasyonu: Kopyala/yapıştır işlemlerinde seçim değişikliklerini takip etme.
- Damage tracking: Pencerenin hangi kısımlarının değiştiğini takip etmeye yardımcı olur (Compositor'lar için önemlidir).

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libXfixes"
    version="6.0.0"
    description="X.Org Xfixes library"
    source="https://www.x.org/archive/individual/lib/libXfixes-$version.tar.gz"
    depends=""
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
