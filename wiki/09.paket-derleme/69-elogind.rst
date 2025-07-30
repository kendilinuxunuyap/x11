**elogind**
===========

Linux’ta oturum (session) yönetimi sağlayan, systemd-logind’in bağımsız bir sürümüdür. Özellikle systemd kullanmayan sistemler için  geliştirilmiştir. Temel işlemleri şunlardır;

1. Kullanıcı oturumlarını izler ve yönetir.
2. Güç olaylarını (suspend, hibernate) destekler.
3. Donanım erişim izinlerini kontrol eder (ses, kamera vb.).
4. D-Bus üzerinden masaüstü ortamlarıyla iletişim kurar.
5. PAM ile kimlik doğrulamayı destekler.
6. Daemon olarak çalışır ve sistemle D-Bus üzerinden iletişim kurar.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #-----------------------------------------------------------------------------------------------------------------
    #!/usr/bin/env bash
    name="elogind"
    version="252.9"
    description="Elogind is the systemd projects logind, extracted to a standalone package"
    source="https://github.com/elogind/elogind/archive/refs/tags/v$version.tar.gz"
    depends="acl,attr,audit,libcap-ng,libcap,dbus,pam,py3-jinja"
    group="sys.auth"
    
    setup(){
        cd $SOURCEDIR
        cp -prfv $PACKAGEDIR/files /tmp/kly/build/   	
        meson setup $BUILDDIR --prefix=/usr --libdir=/lib64/ -Drootlibdir=/lib64 -Dudevrulesdir=/lib64/udev/rules.d \ 
       -Dcgroup-controller=elogind -Dhalt-path=/sbin/halt -Dreboot-path=/sbin/reboot -Dpoweroff-path=/sbin/poweroff \
       -Drootlibexecdir=/usr/libexec/elogind -Ddefault-hierarchy=hybrid -Ddefault-kill-user-processes=true \ 
       -Dpam=true -Dpamconfdir=/etc/pam.d -Dpamlibdir=/usr/lib64/security -Dselinux=false -Daudit=true \
       -Defi=false -Dpolkit=true
    }
    
    build(){
        ninja -C $BUILDDIR
    }
    
    package(){
        cd $DESTDIR
        mkdir -p $DESTDIR/lib64
        ln -s lib64 lib
        mkdir -p "$DESTDIR"/usr/lib64/pkgconfig/
        DESTDIR=$DESTDIR ninja -C $BUILDDIR install
        # Claim compatiblity with systemd and systemd-logind (thanks Alpine linux)
        ln -s libelogind.pc "$DESTDIR"/lib64/pkgconfig/libsystemd.pc
        ln -s libelogind.pc "$DESTDIR"/lib64/pkgconfig/libsystemd-login.pc
        ln -s elogind "$DESTDIR"/usr/include/systemd
        # Extra compatiblity support
        ln -s libelogind.so.0 "$DESTDIR"/lib64/libsystemd.so.0
        ln -s libelogind.so.0 "$DESTDIR"/lib64/libsystemd.so.0.35.0
        ln -s pam_elogind.so "$DESTDIR"/usr/lib64/security/pam_systemd.so
        install ../files/systemd.pc "$DESTDIR"/lib64/pkgconfig/
        # Install headers from elogind
        install -Dm644 $SOURCEDIR/src/systemd/sd-id128.h "$DESTDIR"/usr/include/sd-id128.h
        install -Dm644 $SOURCEDIR/src/systemd/_sd-common.h "$DESTDIR"/usr/include/_sd-common.h
        # openrc service
        mkdir -p "${DESTDIR}"/etc/init.d
        install ../files/elogind.initd "${DESTDIR}"/etc/init.d/elogind
        # shadow system-auth.d file
        mkdir -p "${DESTDIR}"/etc/pam.d/system-auth.d/
        echo "session    include    elogind-user" > "${DESTDIR}"/etc/pam.d/system-auth.d/99-elogind
        # ld.so.conf
        mkdir -p "${DESTDIR}"/etc/ld.so.conf.d/
        echo "/lib64/elogind" > "${DESTDIR}"/etc/ld.so.conf.d/elogind.conf
        cd "$DESTDIR"/usr/lib64/pkgconfig/
        ln -s ../../../lib64/pkgconfig/libelogind.pc libelogind.pc 
    }


.. raw:: pdf

   PageBreak
