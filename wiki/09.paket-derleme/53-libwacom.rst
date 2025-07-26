.. _libwacom:
**libwacom**
============
Linux sistemlerinde wacom tabletleri ve diğer dokunmatik grafik aygıtları için geliştirilmiş bir açık kaynaklı kütüphanedir. Wacom tabletleri ile etkileşimi sağlamak için tasarlanmıştır ve tablet yapılandırmasını, düğme ve kalem hassasiyetini yönetmek için kullanılır.

**Paketi Derleme :**
--------------------

.. code-block:: bash

    #!/usr/bin/env bash
    name="libwacom"
    version="2.10.0"
    url="https://github.com/linuxwacom/libwacom/wiki"
    description="Library to help implement Wacom tablet settings"
    source="https://github.com/linuxwacom/libwacom/releases/download/\
    libwacom-${version}/libwacom-${version}.tar.xz"
    depends="eudev"
    builddepend="meson"
    group="dev.libs"

    setup(){
    	cd $SOURCEDIR
        meson setup $BUILDDIR  \
          --prefix=/usr   \
          --buildtype=release \
          -Dtests=disabled
    }

    build(){
        ninja -C  $BUILDDIR  $jobs
    }

    package(){
       DESTDIR=$DESTDIR ninja -C  $BUILDDIR  install $jobs
    	install -D -m644 COPYING "${DESTDIR}/usr/share/licenses/${name}/LICENSE"
    }

.. raw:: pdf

   PageBreak
