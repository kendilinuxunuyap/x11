.. _libdatrie:
**libdatrie**
=============
Trie (preﬁx tree) veri yapısını kullanan bir C kütüphanesidir. Hızlı arama, önek eşleşmesi (prefix matching) ve sıralama gibi işlemleri gerçekleştiren veritabanlarında ve metin işleme uygulamalarında kullanılır.

- Prefix arama: Trie yapısı sayesinde verilen bir önek (prefix) ile başlayan kelimeleri hızlı bir şekilde bulabilirsiniz.
- Sıralama: Trie yapısındaki veriler doğal sıralıdır, bu yüzden veri sıralaması sağlanabilir.
- Hızlı arama: Trie, özellikle çok büyük veri kümesinde yapılan aramaları çok hızlı hale getirir.
- Bellek verimliliği: Trie yapısında depolanan veriler sıkıştırılabilir, bu da bellek kullanımını optimize eder.



**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libdatrie"
    version="0.2.13"
    description="Implementation of double-array structure for\
     representing trie, as proposed by Junichi Aoe."
    source="https://github.com/tlwg/libdatrie/releases/download/\
    v$version/libdatrie-$version.tar.xz"
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
