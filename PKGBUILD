# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=kf5-phonon-git
pkgver=v4.6.0.384.g2ec59ff
pkgrel=1
pkgdesc='The multimedia framework for KDE'
arch=('i686' 'x86_64')
url='http://phonon.kde.org/'
license=('LGPL')
depends=('qtbase-git' 'phonon-backend' 'libpulse')
optdepends=('pulseaudio: PulseAudio support'
            'qttools-git: QtDesigner Phonon plugin')
makedepends=('cmake' 'pulseaudio' 'git' 'qtquick1-git' 'qttools-git')
provides=('kf5-phonon')
conflicts=('kf5-phonon')
options=('debug')
source=(git://anongit.kde.org/phonon.git)
md5sums=('SKIP')

pkgver() {
  cd phonon
  git describe --always | sed 's|-|.|g' 
}

prepare() {
  mkdir -p build
}

build() {
  export LD_LIBRARY_PATH=/opt/qt-git/lib

  cd build
  cmake ../phonon \
    -DCMAKE_PREFIX_PATH=/opt/qt-git/lib/cmake \
    -DCMAKE_BUILD_TYPE=RelWithDebInfo \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DCMAKE_SKIP_RPATH=ON \
    -DPHONON_BUILD_PHONON4QT5=ON
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
