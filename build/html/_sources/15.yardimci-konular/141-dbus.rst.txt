**D-Bus Yapılandırması**
========================

Bu belge, **systemd kullanmayan** sistemlerde (OpenRC tabanlı) 
D-Bus servisinin kurulumu, yapılandırılması ve başlatılmasını anlatır. 
D-Bus, Linux ortamında uygulamalar arasında mesajlaşma sağlayan
bir IPC (Inter-Process Communication) sistemidir.

**Adım 1: Kullanıcı ve Grup Oluşturma**
---------------------------------------

.. code-block:: bash

    echo "messagebus:x:109:" >> /etc/group
    echo "messagebus:x:103:109::/nonexistent:/usr/sbin/nologin" >> /etc/passwd

**Adım 2: Sistem UUID ve machine-id Ayarı**
-------------------------------------------

.. code-block:: bash

    if [ ! -f /etc/machine-id ] ; then
        dbus-uuidgen --ensure=/etc/machine-id
    fi

**Açıklama**::

- `/etc/machine-id` dosyası sistemin benzersiz kimliğini tutar.
- `dbus-uuidgen --ensure` komutu, dosya yoksa oluşturur, varsa korur.
- Bu kimlik, D-Bus servislerinin ve bazı uygulamaların doğru çalışması için zorunludur.

**Adım 3: dbus-daemon-launch-helper İzin Kontrolü**
---------------------------------------------------

.. code-block:: bash

    if busybox ls /bin/su -la | grep "^...s" >/dev/null ; then
        chmod 4755 /usr/libexec/dbus-daemon-launch-helper
    fi

**Açıklama**::

- `dbus-daemon-launch-helper`, kullanıcı bazlı D-Bus daemonlarını başlatır.
- SUID bitinin (4) set edilmesi, root yetkisi ile çalışmasını sağlar.

**Adım 4: D-Bus Yapılandırma Yenileme**
---------------------------------------

.. code-block:: bash

    dbus-send --system --type=method_call --dest=org.freedesktop.DBus / \
        org.freedesktop.DBus.ReloadConfig >/dev/null 2>&1 || :

**Açıklama**::

- Bu komut, D-Bus sistem servisine yeni yapılandırmaları yüklemesini söyler.
- `--system` parametresi sistem bus’ını hedef alır.
- Hata oluşursa komut sessizce geçer (`|| :`).

.. raw:: pdf

   PageBreak
 
**Adım 5: D-Bus Servisini Başlatma (OpenRC)**
---------------------------------------------

D-Bus için OpenRC init script’i `/etc/init.d/dbus` şu mantıkla çalışır:

.. code-block:: bash

    #!/sbin/openrc-run
    #----------------------------------------------------------------------------------------------
    name="System Message Bus"
    description="An IPC message bus daemon"

    extra_started_commands="reload"

    supervisor=supervise-daemon
    command="/usr/bin/dbus-daemon"
    command_args="--system --nofork --nopidfile --syslog-only ${command_args:-}"
    command_background="yes"
    pidfile="/run/$RC_SVCNAME.pid"

    depend() {
        need localmount
        after bootmisc
    }

    start_pre() {
        mkdir -p /run/dbus
        /usr/bin/dbus-uuidgen --ensure=/etc/machine-id
    }

    stop_post() {
        [ ! -S /run/dbus/system_bus_socket ] || rm -f /run/dbus/system_bus_socket
    }

    reload() {
        ebegin "Reloading $name configuration"
        /usr/bin/dbus-send --print-reply --system --type=method_call \
                --dest=org.freedesktop.DBus \
                / org.freedesktop.DBus.ReloadConfig > /dev/null
        eend $?
    }

**Açıklama**::

- `supervise-daemon`: OpenRC’nin daemon’u denetlemesini sağlar.
- `command` ve `command_args`: D-Bus daemonunu sistem bus modunda başlatır.
- `start_pre()`: Servis başlamadan önce gerekli dizini oluşturur ve machine-id’yi doğrular.
- `stop_post()`: Servis durduğunda socket dosyasını temizler.
- `reload()`: Yapılandırma değişikliklerini uygulamak için D-Bus’a mesaj yollar.
- `depend()`: Servisin başlatılması için gerekli bağımlılıklar (localmount, bootmisc) belirtilir.
- `pidfile`: Servisin PID bilgisini tutar.

**Servis Dosyasının Yaptıklar**::

- D-Bus için sistem kullanıcı ve grup oluşturulur.
- machine-id ve gerekli izinler ayarlanır.
- OpenRC init script’i `/etc/init.d/dbus`, servisin başlatılmasını, durdurulmasını ve yeniden yüklenmesini yönetir.
- `rc-service dbus start` ile sistemde mesajlaşma servisi aktif olur.

**Kaynaklar**::

- D-Bus resmi sitesi:https://www.freedesktop.org/wiki/Software/dbus/  
- D-Bus belgeleri:https://dbus.freedesktop.org/doc/dbus/  
- OpenRC belgeleri:https://wiki.gentoo.org/wiki/OpenRC  
- dbus-daemon ve dbus-send man sayfaları:https://manpages.debian.org/dbus-user-session

.. raw:: pdf

   PageBreak

