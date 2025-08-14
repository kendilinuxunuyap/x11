**dbus**
========
D-Bus, Linux ve diğer Unix benzeri sistemlerde kullanılan bir mesajlaşma sistemidir (inter-process communication - IPC).  Süreçler (Procesler) arasında veri alışverişi yapılmasını sağlar ve sistem ile uygulamalar arasında iletişim kurmak için kullanılır.

- D-Bus, süreçlerin birbirine mesaj göndermesini sağlar. Bu mesajlar, metod çağrıları, sinyaller veya hata mesajları olabilir.
- Sistem genelinde hizmetler (örneğin, donanım yönetimi, ağ servisleri) için kullanılır.
- Kullanıcı oturumuna özgü uygulamalar arasında iletişim için kullanılır (örneğin, masaüstü uygulamaları).
- Çoğu Linux dağıtımında standart olarak bulunur ve masaüstü ortamları (GNOME, KDE) tarafından yaygın şekilde kullanılır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #-------------------------------------------------------------------------------------------
    #!/usr/bin/env bash
    name="dbus"
    version="1.15.2"
    description="A message bus system, a simple way for applications to talk to each other"
    source="https://dbus.freedesktop.org/releases/dbus/dbus-$version.tar.xz"
    depends="audit,expat,libcap-ng,elogind,libX11,libunwind"
    group="sys.apps"
 
    setup(){
    	cp -r ${dizin}/${paket}/files/ /tmp/kly/build/
    	cd $SOURCEDIR
    	./configure --prefix=/usr --libdir=/usr/lib64/ --sysconfdir=/etc  --localstatedir=/var \
            --runstatedir=/run --disable-doxygen-docs --disable-xml-docs --disable-static  \
            --disable-systemd --with-system-pid-file=/run/dbus/dbus.pid --with-x \
            --with-systemduserunitdir=no --with-systemdsystemunitdir=no  \ 
            --with-system-socket=/run/dbus/system_bus_socket
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
        ln -s ../../init.d/xrunsystemd xrunsystemd
        ln -s ../../init.d/dbus dbus
    }

	
Ek dosyaları indirmek için `tıklayınız. <https://kendilinuxunuyap.github.io/_static/files/dbus/files.tar>`_

**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_

.. raw:: pdf

   PageBreak
