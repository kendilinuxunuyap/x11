Dağıtıma özgü ISO oluşturmak için o dağıtımın paket sistemi kullanılır.  
Bu dokümanda anlatılan **kly** paket sistemi, önceki bölümde detaylıca açıklanmıştır.

Bu bölümde, **kly** paket sistemini kullanarak ISO oluşturma adımları basit ve anlaşılır şekilde verilecektir. Aşağıda payşlaşılan script ile hazırlanan iso **/tmp/distro/distro.iso** konumunda olacaktır. Sistemi oluşturan paketleri **github.com/kendilinuxunuyap/kly-base-packages** ve **github.com/kendilinuxunuyap/kly-x11-packages** konumundan indirerek oluşturmaktadır.

**Not:** Anlatılan yöntem genel Linux dağıtımlarının ISO oluşturma mantığına dayanır. Araçlar, dizinler ve komutlarda küçük farklılıklar olabilir, ancak iş akışı aynıdır.

Aşağıdaki scriptle oluşturulmuş iso https://github.com/kendilinuxunuyap/kly-x11-distro/releases/download/current/kly-x11-distro.iso adresinde bulunmaktadır. 

   
**kly Paket Sistemiyle ISO Oluşturma Scripti**
----------------------------------------------

.. code-block:: shell

	#--------------------------------------------------------------------------------------------------------------------
	#!/bin/bash
	set -x
	if which apt &>/dev/null && [[ -d /var/lib/dpkg && -d /etc/apt ]] ; then
		apt-get update
		echo "işlem başladı....."
		apt install xorriso grub-pc-bin grub-efi mtools make python3 dosfstools e2fsprogs squashfs-tools \
		python3-yaml gcc wget curl unzip xz-utils debootstrap git erofs-utils zstd -y
	fi
	apt-get install git devscripts equivs -y
	#--------------------------------------------------------------------------------------------------------------------
	rootfs="/tmp/distro/rootfs"
	distro="/tmp/distro"
	rm -rf $distro/iso
	#rm -rf $rootfs
	mkdir -p /tmp/distro/rootfs
	mkdir -p $rootfs/bin
	#mkdir -p distro/rootfs
	#export PATH=/bbin:$PATH
	cp busybox $rootfs/bin/busybox
	cp kly $rootfs/bin/kly
	cd $rootfs/bin/
	ln -s busybox cpio
	#busybox --install -s ./
	cd $rootfs/
	#cd distro/rootfs/
	mkdir  -p var run dev sys proc etc tmp/kly/kur
	bash -c "echo '127.0.0.1 kly' >> $rootfs/etc/hosts"
	bash -c "echo 'kly' > $rootfs/etc/hostname"
	bash -c "echo 'nameserver 8.8.8.8' > $rootfs/etc/resolv.conf"

	### system chroot  bind/mount
	for i in dev dev/pts proc sys; do mount -o bind /$i $rootfs/$i; done
	### manuel kly-tools install
	$rootfs/bin/busybox wget -O $rootfs/tmp/base-file-1.0.kly https://github.com/bpslinux/\
	kly-temel-paketler/raw/refs/heads/master/base-file/base-file-1.0.kly 1>$rootfs/dev/null 2>$rootfs/dev/null
	$rootfs/bin/busybox tar -xf $rootfs/tmp/base-file-1.0.kly -C $rootfs/tmp/kly/kur
	$rootfs/bin/busybox tar -xf $rootfs/tmp/kly/kur/rootfs.tar.xz -C $rootfs

	#paket adresi ekleniyor
	$rootfs/bin/busybox mkdir -p $rootfs/etc/kly
	echo "kendilinuxunuyap/kly-base-packages">$rootfs/etc/kly/sources.list
	echo "kendilinuxunuyap/kly-x11-packages">>$rootfs/etc/kly/sources.list

	### installing kly package in rootfs
	$rootfs/bin/kly -u $rootfs
	#**********************************************************************
	echo root:x:0:0:root:/root:/bin/sh > $rootfs/etc/passwd 
	chmod 755 $rootfs/etc/passwd
	#**********************************************************************

	for paket in glibc readline ncurses bash openssl acl attr libcap libpcre2 gmp coreutils sqlite  \
	util-linux grep sed mpfr gawk findutils libgcc libcap-ng gzip xz-utils zstd bzip2 elfutils libselinux tar zlib \
	brotli curl
	do
	$rootfs/bin/kly -ri $paket $rootfs
	#chroot $rootfs /bin/kly -ri $paket; 
	done


.. raw:: pdf

   PageBreak
   	
.. code-block:: shell

	#--------------------------------------------------------------------------------------------------------------------
	# scriptin devamı   
	
	for paket in shadow file eudev cpio libsepol kmod audit libxcrypt libnsl libbsd libtirpc \
	e2fsprogs dosfstools initramfs-tools libxml2 expat libmd libaio lvm2 popt icu iproute2 \
	net-tools dhcp openrc rsync kbd kernel dialog live-boot live-config parted busybox nano grub \
	efibootmgr efivar libssh openssh pam 
	do
	#$rootfs/bin/kly -i $paket $rootfs
	chroot $rootfs /bin/kly -ri $paket; 
	done

	# burası x11 için olan paketlerdi. arasınsa ek paket varmı kontrol etmedim. edeceğim
	for paket in xorg-server pixman libpciaccess libXau libXdmcp libXfont2 libxshmfence libdrm libxcvt libfontenc freetype \
	libpng harfbuzz glib \
	xterm libXft fontconfig libXext libXaw libXmu libXinerama libXpm libXt libX11 libICE libXrender libxcb libSM \
	xf86-input-libinput xf86-input-vmmouse xf86-video-amdgpu xf86-video-ast xf86-video-ati xf86-video-dummy \
	xf86-video-fbdev xf86-video-intel \
	xf86-video-mga xf86-video-nouveau xf86-video-qxl xf86-video-r128 xf86-video-siliconmotion xf86-video-vboxvideo \
	xf86-video-vesa xkbcomp libxkbfile libglvnd mesa xkeyboard-config libinput mtdev libevdev libwacom libgudev libffi \
	xinit xcalc libXi openbox libXcursor libXfixes pango libXrandr fribidi xcb-util libthai libdatrie startup-notification \
	dejavu libunwind dbus polkit elogind
	do
	chroot $rootfs /bin/kly -ri $paket; 
	done

	### user add and passwd
	chroot $rootfs echo -e "1\n1\n"|chroot $rootfs passwd root
	chroot $rootfs useradd live -m -s /bin/sh -d /home/live
	chroot $rootfs echo -e "live\nlive\n"|chroot $rootfs passwd live
	for grp in users tty wheel cdrom audio dip video plugdev netdev; do
	chroot $rootfs usermod -aG $grp live || true
	done

	### update-initrd
	fname=$(basename $rootfs/boot/config*)
	kversion=${fname:7}
	mv $rootfs/boot/config* $rootfs/boot/config-$kversion
	cp $rootfs/boot/config-$kversion $rootfs/etc/kernel-config

	chroot $rootfs update-initramfs -u -k $kversion

	#### system chroot umount
	for dir in dev dev/pts proc sys ; do    while umount -lf -R $rootfs/$dir 2>/dev/null ; do true; done done

	#************************iso *********************************
	mkdir -p $distro/iso
	mkdir -p $distro/iso/boot
	mkdir -p $distro/iso/boot/grub
	mkdir -p $distro/iso/live || true

	#### Copy kernel and initramfs (Debian/Devuan)
	cp -pf $rootfs/boot/initrd.img-* $distro/iso/boot/initrd.img
	cp -pf $rootfs/boot/vmlinuz-* $distro/iso/boot/vmlinuz
	rm -rf $rootfs/boot
	#### Create squashfs
	mksquashfs $rootfs $distro/filesystem.squashfs -comp xz -wildcards
	mv $distro/filesystem.squashfs $distro/iso/live/filesystem.squashfs

	# grub.cfg dosyasını yaz
	cat << EOF > "$distro/iso/boot/grub/grub.cfg"
	set timeout=6; set default=1; terminal_input console;
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

	#iso oluşturuluyor
	grub-mkrescue $distro/iso/ -o $distro/distro.iso

Kaynaklar::

	- https://www.subrat.info/build-kernel-and-userspace/ - 08/07/2025
	- https://medium.com/@chienhaotan/compiling-and-running-a-minimal-kernel-with-busybox-bfc45a991017 - 08/07/2025
	- https://wiki.archlinux.org/title/GRUB_(T%C3%BCrk%C3%A7e)  - 08/07/2025
	- https://chatgpt.com/share/6875084c-6050-8012-9229-a37b47351aa2 - 14/07/2025

.. raw:: pdf

   PageBreak



