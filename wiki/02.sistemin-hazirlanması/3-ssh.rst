**Temel Sisteme openssh ile Bağlanma**
--------------------------------------

ssh terminal üzerinden uzak bilgisayarlara erişim yapan bir uygulamadır. **Temel Sistem** içerisinde ssh paketi derlendi ve açılışta aktif hale gelmektedir. ssh kullanımı **Yardımcı Konular** bölümünde anlatılmıştır.

Aşağıda **kly Temel Sisteme ssh** ile erişimin nasıl yapıldığı görülmektedir.

.. image:: /_static/images/ssh.png
  :width: 600

Bu doküman boyunca paketleri **Debian** ortamında derleyeceğiz. Derlediğimiz paketleri **Temel Sistem'e** kopyalacağız. Kopyalama işlemini **ssh** paketi içinde gelen **sftp** veya **scp** ile yapacağız. Kopyalanan paketlerin **kurulması ve kaldırıması** gibi işlemleri **ssh** bağlantısı üzerinden gerçekleştireceğiz.

.. raw:: pdf

   PageBreak
