**kly ile Paket Kaldir**
------------------------

**kly Paket Sistemiyle** sistemde yüklü olan bir paketi **kly -r paketadı** şeklide komut kullanılarak kaldırılabilir. Daha önce paket oluşturma ve paket kurulum işlemlerinde **bash** paketini kullanmıştık. Şimdi **bash** paketini kaldırmamız durumunda sistemde terminali kulanamaz duruma getirecektir. Bazı temel paketleri kaldırmak sistemimizin bozulmasına sebep olabilir. Paket kaldırırken dikkatli olmak gerekir.

Aşağıda **bash** paketinin nasıl kaldırılacağı görülmektedir.

.. image:: /_static/images/kly-paket-kaldir1.png
  :width: 600
  
Bazı paketleri **(glibc, ncurses, readline, bash)** tasarladığımız **kly** paket sisteminde kaldırılmasını engelledik. Bu paketler kalması durumunda sistem kullanılamaz hale gelir. Eğer değişiklik gerekiyorsa sadece yeniden kurulum yapılabilir. Aşağıda paketin kaldırılamadığı mesajı görülmektedir.

.. image:: /_static/images/kly-paket-kaldir2.png
  :width: 600

**glibc, ncurses, readline, bash** dışında başka paketler olsaydı paket kaldırılması gerçekleşecekti.
 
.. raw:: pdf

   PageBreak
