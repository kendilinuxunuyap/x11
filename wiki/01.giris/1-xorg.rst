**Xorg Nedir?**
===============

**Xorg** (veya **X.Org Server**), Unix ve Linux tabanlı işletim sistemlerinde grafiksel kullanıcı arayüzünü (GUI) sağlayan 
**X Pencere Sistemi (X Window System)**’in en yaygın açık kaynaklı uygulamasıdır. Xorg, ekran, klavye, fare gibi 
giriş/çıkış aygıtları ile kullanıcı uygulamaları arasında aracı görevi görerek pencere yönetimini ve grafik çıktıyı sağlar.

**Kısaca Tanımı**
-----------------

Xorg, **X11 protokolünü** temel alarak çalışan bir **görüntü sunucusudur (display server)**. 
Masaüstü ortamlarının (GNOME, KDE, XFCE vb.) çalışmasını sağlar ama kendisi bir masaüstü ortamı değildir.

**Xorg Ne Yapar?**
------------------

- Grafik kartıyla iletişim kurarak pikselleri ekrana yerleştirir.
- Klavye ve fare gibi giriş aygıtlarını işler.
- Pencereleri yönetmez ama pencere yöneticilerinin çalışmasını sağlar.
- Uzaktaki makinelerden grafik uygulamalarını çalıştırabilir (X forwarding).

**Temel Bileşenler**
--------------------

Xorg, aşağıdaki bileşenleri içerebilir veya bunlarla birlikte çalışır:

- ``xorg.conf``: Yapılandırma dosyası (modern sistemlerde genellikle otomatik yapılandırma kullanılır).
- **DRI/DRM**: *Direct Rendering Infrastructure / Direct Rendering Manager*; doğrudan donanım erişimi.
- **Mesa**: Açık kaynak OpenGL implementasyonu.
- **Xlib**, **XCB**: X protokolünü kullanan programlama arabirimleri.

**Yapılandırma Dosyaları**
--------------------------

- ``/etc/X11/xorg.conf`` (eski sistemlerde)
- ``/etc/X11/xorg.conf.d/`` dizini altındaki parçalı yapılandırmalar
- Modern sistemlerde otomatik olarak ``/var/log/Xorg.0.log`` dosyasına günlük yazar

**Kaynaklar**
-------------

- `X.Org Foundation – Resmi Site <https://www.x.org/>`__
- `X.Org Server GitHub <https://gitlab.freedesktop.org/xorg/xserver>`__
- `Arch Wiki – Xorg <https://wiki.archlinux.org/title/Xorg>`__
- `Gentoo Wiki – Xorg Guide <https://wiki.gentoo.org/wiki/Xorg/Guide>`__

.. raw:: pdf

   PageBreak
