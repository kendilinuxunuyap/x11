D-Bus (Desktop Bus)
====================

D-Bus (Desktop Bus), Linux ve Unix benzeri işletim sistemlerinde farklı uygulamaların ve süreçlerin (process) birbiriyle iletişim kurmasını sağlayan bir IPC (Inter-Process Communication) sistemidir.


**Örnek kullanım alanlarına :**

- Masaüstü uygulamaları arasında haberleşme (örneğin, bir medya oynatıcının durumu sistem çubuğuna bildirmesi).
- Sistem servisleriyle kullanıcı uygulamaları arasında iletişim (örneğin, ``NetworkManager`` servisinden ağ durumunu sorgulamak).

**dbus paketi derleme :**
-------------------------
Debian'da dbus paketi derlemek için aşağıdaki paketlerin kurulu olası gerekir.

.. code-block:: bash


    sudo apt install build-essential autoconf automake libtool pkg-config libexpat1-dev python3

.. code-block:: bash

    #--------------------------------------------------------------------------------------------------------------------
    #!/usr/bin/env bash
    name="dbus"
    version="1.15.2"
    description="A message bus system, a simple way for applications to talk to each other"
    source="https://dbus.freedesktop.org/releases/dbus/dbus-$version.tar.xz"
    depends="audit,expat,libcap-ng,elogind,libX11,libunwind"
    group="sys.apps"
 
    setup(){
    	mkdir -p /tmp/bps/build/files
    	cp -r ${dizin}/${paket}/files /tmp/kly/build/
    	cd $SOURCEDIR
    	./configure --prefix=/usr --libdir=/usr/lib64/ --sysconfdir=/etc --localstatedir=/var \
            --runstatedir=/run --disable-doxygen-docs --disable-xml-docs --disable-static \
            --disable-selinux --with-system-pid-file=/run/dbus/dbus.pid --with-x --with-systemduserunitdir=no \
            --with-systemdsystemunitdir=no --with-system-socket=/run/dbus/system_bus_socket
    }
    
    build(){
        make
    }
    
    package(){
        make install DESTDIR=$DESTDIR
        mkdir -p "$DESTDIR"/etc/init.d "$DESTDIR"/etc/local.d "$DESTDIR"/etc/X11/xinit/xinitrc.d/
        install ../files/dbus.initd "$DESTDIR"/etc/init.d/dbus
        install ../files/dbus.xinit "$DESTDIR"/etc/X11/xinit/xinitrc.d/30-dbus-launch.sh
        install ../files/xrunsystemd.init.d ${DESTDIR}/etc/init.d/xrunsystemd
        install ../files/runsystemd.local.d ${DESTDIR}/etc/local.d/runsystemd
        
         for level in boot default nonetwork shutdown sysinit ; do
        mkdir -p ${DESTDIR}/etc/runlevels/$level
        done
        cd ${DESTDIR}/etc/runlevels/default
        ln -s ../init.d/xrunsystemd xrunsystemd
        ln -s ../init.d/dbus dbus
    }


dbus paketini yapmak için gereken ek dosyaları indirmek için tıklayınız. dbus adlı bir dizin oluşturup içine indirdiğiniz files.tar.gz dosyasını açın ve dbus derleme scriptini klybuild dosyası olarak bu dizine kaydedin ve aşağıdaki komut ile paketleme işlemini yapın.

.. code-block:: bash

    fakeroot klypaketle dbus/

komut hata vermeden tamamlanırsa dbus dizini içinde **"dbus-1.15.2.kly"**  paketi kopyalanır.

.. raw:: pdf

   PageBreak
