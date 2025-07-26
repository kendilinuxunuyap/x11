**kly ile Paket Yapma**
-----------------------

kly paket sistemi ile paket yapma işlemini Debian ortamında yapacağız. Debian üzerinde paket sistemimizi oluşturan scriptimiz **/bin/kly** konumunda olması gerekmektedir.

Şimdi **bash** paketinin **kly Paket Sistemi**'ni kullanarak derlemesini yapalım. Paket için aşağıda görüldüğü gibi masaüstüne **kly-paket** dizini oluşturuldu. **kly-paket**  dizini içine **bash** dizini oluşturuldu. **bash** dizini içine **klybuild** dosyası oluşturuldu.

.. image:: /_static/images/kly-paket-yap1.png
  :width: 600
 
**klybuild** dosyasının içerine aşağıdaki kodu ekleyiniz.

.. code-block:: bash

	#!/usr/bin/env bash
	version="5.2.21"
	name="bash"
	depends="glibc,readline,ncurses"
	description="GNU/Linux dağıtımında ön tanımlı kabuk"
	source="https://ftp.gnu.org/pub/gnu/bash/${name}-${version}.tar.gz"
	groups="app.shell"
	setup()	{
		cd $SOURCEDIR
		./configure --prefix=/usr --libdir=/usr/lib64 	--bindir=/bin \
			--with-curses --enable-readline	--without-bash-malloc
	}
	build()	{
		make 
	}
	package()	{
		make install DESTDIR=$DESTDIR
		cd $DESTDIR/bin
		ln -s bash sh
	}

**Not:** Bazı paketlerde ek dosyalar olacaktır. Bu paketlerin derleme scriplerinin altında **Ek dosya için tıklayınız** bağlantı(link) göreceksiniz. Bu bağlantıdan ek dosyalrı indirin ve paketin dizini içine sıkıştırılmış dosyayı arşivde çıkartınız. Burada örneğimiz **bash** paketi olduğu için eğer ek dosyaları olsaydı **bash** dizini içine indiğimiz dosyayı  arşivde çıkartacaktık(klybuil dosyasıyla aynı konumda olacak). 

.. raw:: pdf

   PageBreak
   
**kly-paket** dizini konumunda aşağıdaki gibi terminal açınız. 

.. image:: /_static/images/kly-paket-yap2.png
  :width: 600

Açılan terminalde aşağıda görüldüğü gibi komutu çalıştırınız. komut hangi konumda çalıştırılmışsa **.kly** uzantılı pakeyimiz orada oluşacaktır. Siz istediğiniz yerde çalıştırabilirsiniz. Önemli olan paket için oluştuduğunuz **klybuild** dosyanınızın konumunu doğru vermeniz.

.. image:: /_static/images/kly-paket-yap3.png
  :width: 600
  
.. raw:: pdf

   PageBreak

Aşağıda **bash** dizinini parametre olarak vererek **bash** paketimizin derlemesini başlatıyoruz.

.. image:: /_static/images/kly-paket-yap4.png
  :width: 600

Derleme işlemi paketin büyüklüğüne bağlı olarak zaman alacaktır. Paket derlemesi bittikten sonra aşağıda görüldüğü gibi termina çıktısı almalısınız. Sorun çıkması durumunda terminalde hata mesajları alırsınız.

.. image:: /_static/images/kly-paket-yap5.png
  :width: 600
  
Derleme işlemi bittikten sonra **kly-paket/bash** dizini komununda  aşağıda görüldüğü gibi **bash-5.2.21.kly** paketimizi oluşturacaktır.

.. image:: /_static/images/kly-paket-yap6.png
  :width: 600
  
.. raw:: pdf

   PageBreak
