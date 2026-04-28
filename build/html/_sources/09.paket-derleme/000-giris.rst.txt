.. _giris:

**Ön Hazırlık**
---------------

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


GNU Araçlarıyla **xorg ve x11** derleme işlemini **kly Paket Sistemi** kullanılarak derleyeceğiz. Derleme işlemini **kly -c** komutuyla yapacağız. Derlenen paketleri **scp** ve **sftp** kullanarak **Temel Sistem** üzerine kopyalayacağız. **kly -i** komutumuzla
kopyaladığımız paketi **Temel Sistem** üzerine kuracağız. Oluşturduğumuz paketleri istersek github'a yükleyip. github üzerinden kururabiliriz.

.. raw:: pdf

   PageBreak


**xorg ve x11'in Çalışması için Gerekli Paketler**
--------------------------------------------------

.. list-table::
   :widths: 33 33 33

   * - 0- :ref:`giris`
     - 25- :ref:`libX11`
     - 50- :ref:`libinput`
   * - 1- :ref:`xorg-server`
     - 26- :ref:`libICE`
     - 51- :ref:`mtdev`
   * - 2- :ref:`pixman`
     - 27- :ref:`libXrender`
     - 52- :ref:`libevdev`
   * - 3- :ref:`libpciaccess`
     - 28- :ref:`libxcb`
     - 53- :ref:`libwacom`
   * - 4- :ref:`libXau`
     - 29- :ref:`libSM`
     - 54- :ref:`libgudev`
   * - 5- :ref:`libXdmcp`
     - 30- :ref:`xf86-input-libinput`
     - 55- :ref:`libffi`
   * - 6- :ref:`libXfont2`
     - 31- :ref:`xf86-input-vmmouse`
     - 56- :ref:`xinit`
   * - 7- :ref:`libxshmfence`
     - 32- :ref:`xf86-video-amdgpu`
     - 57- :ref:`xcalc`
   * - 8- :ref:`libdrm`
     - 33- :ref:`xf86-video-ast`
     - 58- :ref:`libXi`
   * - 9-  :ref:`libxcvt`
     - 34- :ref:`xf86-video-ati`
     - 59- :ref:`openbox`
   * - 10- :ref:`libfontenc`
     - 35- :ref:`xf86-video-dummy`
     - 60- :ref:`libXcursor`
   * - 11- :ref:`freetype`
     - 36- :ref:`xf86-video-fbdev`
     - 61- :ref:`libXfixes`
   * - 12- :ref:`libpng`
     - 37- :ref:`xf86-video-intel`
     - 62- :ref:`pango`
   * - 13- :ref:`harfbuzz`
     - 38- :ref:`xf86-video-mga`
     - 63- :ref:`libXrandr`
   * - 14- :ref:`glib`
     - 39- :ref:`xf86-video-nouveau`
     - 64- :ref:`fribidi`
   * - 15- :ref:`xterm`
     - 40- :ref:`xf86-video-r128`
     - 65- :ref:`xcb-util`
   * - 16- :ref:`libXft`
     - 41- :ref:`xf86-video-siliconmotion`
     - 66- :ref:`libthai`
   * - 17- :ref:`fontconfig`
     - 42- :ref:`xf86-video-vboxvideo`
     - 67- :ref:`libdatrie`
   * - 18- :ref:`dejavu`
     - 43- :ref:`xf86-video-vesa`
     - 68- :ref:`dbus`
   * - 19- :ref:`libXext`
     - 44- :ref:`xf86-video-vmware`
     - 69- :ref:`elogind`
   * - 20- :ref:`libXaw`
     - 45- :ref:`xkbcomp`
     - 70- :ref:`libunwind`
   * - 21- :ref:`libXmu`
     - 46- :ref:`libxkbfile`
     - 71- 
   * - 22- :ref:`libXinerama`
     - 47- :ref:`libglvnd`
     - 72- 
   * - 23- :ref:`libXpm`
     - 48- :ref:`startup-notification`
     - 73-    
   * - 24- :ref:`libXt`
     - 49- :ref:`xkeyboard-config`
     - 74-

**Bağımlılık Zinciri**
----------------------

Linux paketinin sorunsuz çalışabilmesi için bağımlı olduğu tüm paketlerin önceden derlenmiş olması gerekir. 
**x11**'in en temel paketleri **xorg-server, mesa, llvm, cairo** paketleridir.  Tüm paketleri derlesek bile **xorg-server, mesa, llvm, cairo** paketleri düzgün ve uyumlu versiyonları olmadığı zaman x penceremiz açılmayacaktır. Buradaki tüm paketler ve bağımlılıkları derlendikten sonra **Xorg:0** şeklinde x pencere sistemimiz çalışacaktır.

**Derleme Öncesi Hazırlık!**
----------------------------

Paket derleme işlemine başlamadan önce, aşağıdaki temel araçları sisteminize kurmalısınız.

.. code-block:: bash

	sudo apt update
	sudo apt-get install debootstrap xorriso mtools make squashfs-tools gcc wget unzip xz-utils tar zstd fakeroot \
	autoconf automake autotools-dev make meson cmake ninja-build pkgconf patch libtool grub-pc grub-pc-bin
	
.. raw:: pdf

   PageBreak

