.. _startup-notification:
**startup-notification**
========================
Bilgilendirme(uygulama mesajları) için kullanılan bir pakettir.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="startup-notification"
    version="0.12"
    description="Application startup notification and feedback library "
    source="http://www.freedesktop.org/software/startup-notification/\
    releases/startup-notification-${version}.tar.gz"
    depends="libX11,xcb-util"
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
