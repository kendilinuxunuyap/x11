.. _startup-notification:
**startup-notification**
========================
Bir uygulamanın başlatılma süreci sırasında kullanıcıya görüntülü bildirimde bulunma amacıyla kullanılan bir X11 uzantısıdır. Bu uzantı, uygulama başlatıldığında, özellikle yavaş başlatan uygulamalarda kullanıcıyı bilgilendirir ve etkileşimli bir geri bildirim sağlar.

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

    cd startup-notification-$version

    setup(){
    	autoreconf -fvi
        $SOURCEDIR/configure --prefix=/usr \
            --libdir=/usr/lib64/
    }

    build(){
        make
    }

    package(){
        make install DESTDIR=$DESTDIR
    }

.. raw:: pdf

   PageBreak
