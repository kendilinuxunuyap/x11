**Temel Sistem ve Paket Sistemi(kly)**
-----------------------------------------

Paket sistemi, sisteme paket **(kurma, kaldırma, index güncelleme)** gibi temel işlemlerin yapılmasını sağlar. Bu temel işlemleri yapacak **Temel Sistem** üzerinde **base-file** paketinden gelen scriptlerimiz yüklü olarak gelmektedir. **Yardımcı Konular** bölümünde  paket sisteminin nasıl kullanılacağı anlatılmıştır.

Aşağıda **kly Temel Sistem** üzerinde hazır gelen paket sistemi uygulamalarımız görülmektedir.

.. image:: /_static/images/kly-paket-sistemi.png
  :width: 600

- klypaketle: kly paketi oluşturur.
- klykur: kly paketini sisteme kurar.
- klykaldir: Sistemde kurulu olan paketi kaldırır.
- klyupdate: github üzerinden güncel paket listelerini sistemde günceller. 

GNU Araçlarıyla xorg ve x11 Derleme konu başlığı altında paketleri **kly Paket Sistemi** kullanılarak derleyeceğiz. Derleme işlemini  **klypaketle** komutuyla yapacağız. Derlenen paketleri **scp** ve **sftp** kullanarak **Temel Sistem** üzerine kopyalayacağız. **klykur** komutumuzla kopyaladığımız paketi **Temel Sistem** üzerine kuracağız. Oluşturduğumuz paketleri istersek(daha doğru bir yöntem) github'a yükleyip. github üzerinden kururabiliriz. Oluşturulan pakeketlerin github üzerine nasıl yükleneceği **Yardımcı Konular** bölümünde **Paketlerin Githuba Yüklenemesi** başlığı altında anlatıldı.


.. raw:: pdf

   PageBreak
