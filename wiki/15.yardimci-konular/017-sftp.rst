**sftp ile Sanal Makinaya Bağlanma**
====================================

SFTP (Secure File Transfer Protocol), SSH protokolü üzerinden güvenli dosya transferi yapmayı sağlar. 
Bir sanal makinaya bağlanarak dosya alışverişi yapmak için aşağıdaki adımları takip edebilirsiniz.

**1. SSH Sunucusunun Kurulu ve Çalışır Olmalıdır**
--------------------------------------------------

SFTP, SSH servisi üzerinden çalışır. Sanal makinede SSH sunucusunun yüklü ve aktif olması gerekir.

.. code-block:: bash

   sudo rc-status sshd

Eğer kurulu değilse:

.. code-block:: bash

    klykur openssh


**2. Sanal Makinanın IP Adresini Öğren**
----------------------------------------

Sanal makine içinde aşağıdaki komutlardan biriyle IP adresini öğrenilir:

.. code-block:: bash

   ip a

veya

.. code-block:: bash

   hostname -I

Örnek IP adresi:

.. code-block:: text

   192.168.1.101

**3. SFTP ile Bağlantı Kur**
----------------------------

Ana makineden terminal açarak aşağıdaki komut ile SFTP bağlantısı başlatılır:

.. code-block:: bash

   sftp kullanıcı_adı@ip_adresi

Örnek:

.. code-block:: bash

   sftp kly@192.168.1.101

Bağlandıktan sonra şu ekranı görürsünüz:

.. code-block:: text

   sftp>

Aşağıdaki komutları kullanabilirsiniz:

- **ls** : Uzak sunucudaki dizin içeriğini listeler.
- **lcd /yerel/yol** : Yerel sistemdeki dizini değiştirir.
- **cd /uzak/yol** : Uzak sunucudaki dizini değiştirir.
- **get dosya.txt** : Uzak dosyayı indirir.
- **put dosya.txt** : Yerel dosyayı sunucuya yükler.
- **exit** : Bağlantıyı sonlandırır.

**4. Grafik Arayüz SFTP Alternatifleri**
------------------------------------------------

Linux ortamlarında, dosya yöneticileri ve FTP programları ile de SFTP bağlantısı kurulabilir.

**GNOME Nautilus / Cinnamon Nemo** ile SFTP bağlantısı için:

Adres çubuğuna bağlantı bilgisi şu formatta yazılır:

.. code-block:: text

   sftp://kly@192.168.1.101

**FileZilla** gibi bir ftp programı ile aşağıdaki ayarlar kullanılarak SFTP bağlantısı yapılır:

- Host: `sftp://192.168.1.101`
- Username: `kly`
- Password: şifre
- Port: `22`

--------------------------------------------

Not: Sanal makinenizin ağ ayarlarının (NAT veya Bridged) ve güvenlik duvarı yapılandırmasının doğru olması gerekir.

.. raw:: pdf

   PageBreak

