Dağıtıma özgü ISO oluşturmak için o dağıtımın paket sistemi kullanılır.  
Bu dokümanda anlatılan **kly** paket sistemi, önceki bölümde detaylıca açıklanmıştır.

Bu bölümde, **kly** paket sistemini kullanarak ISO oluşturma adımları basit ve anlaşılır şekilde verilecektir. Aşağıda payşlaşılan script ile hazırlanan iso **/tmp/distro/distro.iso** konumunda olacaktır. Sistemi oluşturan paketleri **github.com/kendilinuxunuyap/kly-binary-packages** konumundan indirerek oluşturmaktadır.


**Not:** Anlatılan yöntem genel Linux dağıtımlarının ISO oluşturma mantığına dayanır. Araçlar, dizinler ve komutlarda küçük farklılıklar olabilir, ancak iş akışı aynıdır.


   
**kly Paket Sistemiyle ISO Oluşturma Scripti**
----------------------------------------------

.. code-block:: shell

	#--------------------------------------------------------------------------------------------------------------------
	#!/bin/bash
	rootfs="/tmp/distro/rootfs"
	distro="/tmp/distro"
	rm -rf $rootfs
	mkdir -p $rootfs -p $rootfs/bin $rootfs/etc
	##Kurulum scripti
	cp -prf files/bin/* $rootfs/bin/
	cp -prf files/etc/* $rootfs/etc/
	
	# temel dizinler ve dosyalar oluşturuluyor
	cd $rootfs/
	mkdir  -p bin dev etc home lib64 proc root run sbin sys usr var etc/kly \
	tmp tmp/kly/kur var/log  var/tmp usr/lib64/x86_64-linux-gnu \
	usr/lib64/pkgconfig usr/local/{bin,etc,games,include,lib,sbin,share,src}
	ln -s lib64 lib
	cd var&&ln -s ../run run&&cd -
	cd usr&&ln -s lib64 lib&&cd -
	cd usr/lib64/x86_64-linux-gnu&&ln -s ../pkgconfig  pkgconfig&&cd -

	echo -e "/bin/sh\n/bin/bash\n/bin/rbash\n/bin/dash" >> "$rootfs/etc/shell"
	echo "tmpfs /tmp tmpfs rw,nodev,nosuid 0 0" >> "$rootfs/etc/fstab"
	echo "127.0.0.1 kly" >> "$rootfs/etc/hosts"
	echo "kly" > "$rootfs/etc/hostname"
	echo "nameserver 8.8.8.8" > "$rootfs/etc/resolv.conf"

	# paket adresi ekleniyor
	echo "kendilinuxunuyap/kly-binary-packages">$rootfs/etc/kly/sources.list

	### installing kly create_package in rootfs
	echo root:x:0:0:root:/root:/bin/sh > $rootfs/etc/passwd 
	chmod 755 $rootfs/etc/passwd

	### system chroot  bind/mount
	for dir in dev dev/pts proc sys; do mount -o bind /$dir $rootfs/$dir; done
	## paket listesi güncelleniyor
	$rootfs/bin/klyupdate $rootfs

	## paketler kuruluyor
	for paket in glibc readline ncurses \bash openssl acl attr libcap libpcre2 gmp \
	 coreutils util-linux \grep \sed mpfr \gawk findutils libgcc libcap-ng sqlite \
	 \gzip xz-utils zstd \bzip2 \elfutils libselinux \tar \zlib brotli curl shadow \ 
	 \file eudev cpio libsepol kmod audit libxcrypt libnsl pam libtirpc e2fsprogs \
	 dosfstools  initramfs-tools libxml2 expat libmd libaio lvm2 popt icu iproute2 \
	 net-tools  dhcp openrc  rsync kbd busybox kernel kernel-headers live-boot \ 
	 live-config parted  nano grub dialog efibootmgr efivar libssh openssh
	do
	chroot $rootfs /bin/klykur $paket; 
	done

	#### system chroot umount
	for dir in dev dev/pts proc sys ; do    while umount -lf -R $rootfs/$dir \
	2>/dev/null ; do true; done done
	exit


.. raw:: pdf

   PageBreak

.. code-block:: shell

	#--------------------------------------------------------------------------------------------------------------------
	# scriptin devamı   
	chroot $rootfs useradd live -m -s /bin/sh  -d /home/live
	chroot $rootfs echo -e "live\nlive\n"|chroot $rootfs passwd live

	for grp in users tty wheel cdrom audio dip video plugdev netdev; do
		chroot $rootfs usermod -aG $grp live || true
	done

	sed -i "/agetty_options/d" $rootfs/etc/conf.d/agetty
	echo -e "\nagetty_options=\"-l /usr/bin/login\"" >> $rootfs/etc/conf.d/agetty

	### update-initrd
	fname=$(basename $rootfs/boot/config*)
	kversion=${fname:7}
	mv $rootfs/boot/config* $rootfs/boot/config-$kversion
	cp $rootfs/boot/config-$kversion $rootfs/etc/kernel-config

	chroot $rootfs update-initramfs -u -k $kversion
	#### system chroot umount
	for dir in dev dev/pts proc sys ; 
	do    while umount -lf -R $rootfs/$dir 2>/dev/null ; do true; done done

	mkdir -p "$distro/iso" "$distro/iso/boot" "$distro/iso/boot/grub"
	mkdir -p  "$distro/iso/live"
	#### Copy kernel and initramfs
	cp -pf $rootfs/boot/initrd.img-* $distro/iso/boot/initrd.img
	cp -pf $rootfs/boot/vmlinuz-* $distro/iso/boot/vmlinuz
	rm -rf $rootfs/boot

	#### Create squashfs
	mksquashfs $rootfs $distro/filesystem.squashfs -comp xz -wildcards
	mv $distro/filesystem.squashfs $distro/iso/live/filesystem.squashfs

	#### Write grub.cfg
	cat << EOF > "$distro/iso/boot/grub/grub.cfg"
	set timeout=3	# Timeout for menu
	set default=1	# Default boot entry

	# Menu Colours
	set menu_color_normal=white/black
	set menu_color_highlight=white/blue
	insmod all_video
	terminal_output console
	terminal_input console
	menuentry "Canli(live) GNU/Linux 64-bit" --class liveiso {
		linux /boot/vmlinuz boot=live init=/sbin/openrc-init net.ifnames=0 \
		biosdevname=0
		initrd /boot/initrd.img
	}
	menuentry "Kur GNU/Linux 64-bit" --class liveiso {
		linux /boot/vmlinuz boot=live init=/bin/kur quiet
		initrd /boot/initrd.img
	}
	EOF
	grub-mkrescue $distro/iso/ -o $distro/distro.iso

Kaynaklar::

	- https://www.subrat.info/build-kernel-and-userspace/ - 08/07/2025
	- https://medium.com/@chienhaotan/compiling-and-running-a-minimal-kernel-with-busybox-bfc45a991017 - 08/07/2025
	- https://wiki.archlinux.org/title/GRUB_(T%C3%BCrk%C3%A7e)  - 08/07/2025
	- https://chatgpt.com/share/6875084c-6050-8012-9229-a37b47351aa2 - 14/07/2025

.. raw:: pdf

   PageBreak



