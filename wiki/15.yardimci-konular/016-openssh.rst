**ssh ile Sanal Makinaya Bağlanma**
===================================

Bir sanal makineye (**VM**) SSH üzerinden bağlanmak, uzak sistem yönetimi için yaygın ve güvenli bir yöntemdir. 
Aşağıdaki adımları takip ederek sanal makinana kolayca bağlanabilirsin.

**1. SSH Sunucusunun Kurulu ve Çalışır Olmalıdır**
--------------------------------------------------

**Temel Sistem:**

.. code-block:: bash

   klykur openssh
   rc-update add sshd
   rc-servise sshd start


**2. Sanal Makina IP Adresi**
-----------------------------

SanalMakina içerisinde aşağıdaki komutlardan biriyle IP adresini öğrenilir:

.. code-block:: bash

   ip a

veya

.. code-block:: bash

   hostname -I

Örnek IP adresi:

.. code-block:: text

   192.168.1.101

**3. sshd_config Dosyasını Düzenle**
------------------------------------

/etc/ssh/sshd_config config dosyasını nano ile açıp,

.. code-block:: text

   nano /etc/ssh/sshd_config

**#PermitRootLogin prohibit-password**  satırını

**PermitRootLogin yes** olarak değiştirilir.

**4. SSH ile Bağlantı Kur**
---------------------------

Ana sistemden terminal açarak aşağıdaki komut ile SSH bağlantısı yapılır:

.. code-block:: bash

   ssh kullanıcı_adı@ip_adresi

Örnek:

.. code-block:: bash

   ssh kly@192.168.1.101

İlk bağlantıda şu uyarıyı verebilir:

.. code-block:: text

   Are you sure you want to continue connecting (yes/no/[fingerprint])?

**yes** yazıp enter'a basılıp, şifreyi girildiğinde **SSH** bağlantısı hazır olur.


.. raw:: pdf

   PageBreak
