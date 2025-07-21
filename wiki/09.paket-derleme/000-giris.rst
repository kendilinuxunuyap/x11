**Kurulum Dizini: Dağıtımın Oluşacağı Yer**
-------------------------------------------

Paket derleme işlemi öncesi aşağıdaki konuları bilmemiz gerekmektedir. Bunlar; 

1. Derleme(Dinamik/Static) 
2. chroot Kullanımı 
3. İso Oluşturma
4. ssh Kullanımı
5. sftp Kullanımı
6. scp Kullanımı
7. VirtualBox Kullanmı
8. cfdisk Kullanımı

Burada liste halinde verilen konu başlıkları bu dokümanın **Yardımcı Konular** bölümünde anlatılmaktadır. 

Bundan sonraki adımlarda kendi dağıtımımızın **xorg ve x11** pencere sistemini derleyerek **Temel Sistem** üzerinde çalıştıracağız!


.. raw:: pdf

   PageBreak


**xorg ve x11 İçin İhtiyacımız Olan Paketler**
-----------------------------------------------

.. list-table::
   :widths: 25 25 50

   * - 0- :ref:`base-file`
     - 25- :ref:`elfutils`
     - 50- :ref:`popt`
   * - 1- :ref:`glibc`
     - 26- :ref:`libselinux`
     - 51- :ref:`icu`
   * - 2- :ref:`readline`
     - 27- :ref:`tar`
     - 52- :ref:`iproute2`
   * - 3- :ref:`ncurses`
     - 28- :ref:`zlib`
     - 53- :ref:`net-tools`
   * - 4- :ref:`bash`
     - 29- :ref:`brotli`
     - 54- :ref:`dhcp`
   * - 5- :ref:`openssl`
     - 30- :ref:`curl`
     - 55- :ref:`openrc`
   * - 6- :ref:`acl`
     - 31- :ref:`shadow`
     - 56- :ref:`rsync`
   * - 7- :ref:`attr`
     - 32- :ref:`file`
     - 57- :ref:`kbd`
   * - 8- :ref:`libcap`
     - 33- :ref:`eudev`
     - 58- :ref:`kernel`
   * - 9-  :ref:`libpcre2`
     - 34- :ref:`cpio`
     - 59- :ref:`dialog`
   * - 10- :ref:`gmp`
     - 35- :ref:`libsepol`
     - 60- :ref:`live-boot`
   * - 11- :ref:`coreutils`
     - 36- :ref:`kmod`
     - 61- :ref:`live-config`
   * - 12- :ref:`util-linux`
     - 37- :ref:`audit`
     - 62- :ref:`parted`
   * - 13- :ref:`grep`
     - 38- :ref:`libxcrypt`
     - 63- :ref:`busybox`
   * - 14- :ref:`sed`
     - 39- :ref:`libnsl`
     - 64- :ref:`nano`
   * - 15- :ref:`mpfr`
     - 40- :ref:`libbsd`
     - 65- :ref:`grub`
   * - 16- :ref:`gawk`
     - 41- :ref:`libtirpc`
     - 66- :ref:`efibootmgr`
   * - 17- :ref:`findutils`
     - 42- :ref:`e2fsprogs`
     - 67- :ref:`efivar`
   * - 18- :ref:`gcc`
     - 43- :ref:`dosfstools`
     - 68- :ref:`libssh`
   * - 19- :ref:`libcap-ng`
     - 44- :ref:`initramfs-tools`
     - 69- :ref:`openssh`
   * - 20- :ref:`sqlite`
     - 45- :ref:`libxml2`
     - 70- :ref:`pam`
   * - 21- :ref:`gzip`
     - 46- :ref:`expat`
     - 71- 
   * - 22- :ref:`xz-utils`
     - 47- :ref:`libmd`
     - 72- 
   * - 23- :ref:`zstd`
     - 48- :ref:`libaio`
     - 73-    
   * - 24- :ref:`bzip2`
     - 49- :ref:`lvm2`
     - 74-

**Bağımlılık Zinciri**
----------------------

Linux paketinin sorunsuz çalışabilmesi için bağımlı olduğu tüm paketlerin önceden derlenmiş olması gerekir. 
**x11**'in en temel paketleri **xorg-server, mesa, llvm, cairo** paketleridir.  Tüm paketleri derlesek bile **xorg-server, mesa, llvm, cairo** paketleri düzgün ve uyumlu versiyonları olmadığı zaman x penceremiz açılmayacaktır. Buradaki tüm paketler ve bağımlılıkları derlendikten sonra **Xorg:0** şeklinde x pencere sistemimiz çalışacaktır.

**Hazırlık: Gerekli Derleme Araçlarını Kurun!**
-----------------------------------------------

Paket derleme işlemine başlamadan önce, aşağıdaki temel araçları sisteminize kurmalısınız.

.. code-block:: bash

	sudo apt update
	sudo apt-get install debootstrap xorriso mtools make squashfs-tools gcc wget unzip xz-utils tar zstd fakeroot \
	autoconf automake autotools-dev make meson cmake ninja-build pkgconf patch libtool grub-pc grub-pc-bin
	
.. raw:: pdf

   PageBreak

