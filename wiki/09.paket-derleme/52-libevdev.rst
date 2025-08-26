.. _libevdev:
**libevdev**
============
Linux tabanlı sistemlerde, evdev (event device) tabanlı giriş aygıtlarını (fareler, klavyeler, dokunmatik ekranlar vb.) yönetmek için kullanılan bir C kütüphanesidir. libevdev, giriş olaylarını okuma, yazma ve yapılandırma işlemleri sağlar ve bu sayede evdev aygıtları ile etkileşimi kolaylaştırır.


**Paketi Derleme :**
--------------------

Debian'da paketi derlemek için aşağıdaki paketlerin kurulu olması gerekir.

.. code-block:: bash

	sudo apt install doxygen
	
.. code-block:: bash

    #!/usr/bin/env bash
    name="libevdev"
    version="1.13.1"
    description="Wrapper library for evdev devices"
    source="https://gitlab.freedesktop.org/libevdev/libevdev/-/archive/\
    libevdev-$version/libevdev-libevdev-$version.tar.gz"
    depends=""
    builddepend="doxygen,meson,python3"
    group="sys.libs"

    setup(){
        cd $SOURCEDIR
        meson setup $BUILDDIR \
        	--prefix=/usr \
            --libdir=/usr/lib \
        	-Db_lto=true \
    		-Dtests=disabled \
    		-Ddocumentation=enabled \
    		-Dcoverity=false
    }

    build(){
        ninja -C $BUILDDIR
    }

    package(){
        DESTDIR=$DESTDIR ninja -C $BUILDDIR install
    }


**Not:** Burada verilen derleme talimatı(script) **kly Paket Sistemi**'ni kullanarak paketi derler ve oluştur. Oluşan paket(**.kly uzantılı dosya**)  **kly Paket Sistemi** kullanılarak siteme yüklenebilir. **kly Paket Sistemiyle Paket Yapma** konusunu okumak için `tıklayınız. <#klypaketyap>`_


.. raw:: pdf

   PageBreak
