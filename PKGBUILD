# Maintainer: Alberto Fanjul <albertofanjul@gmail.com>
pkgname=miraclecast
_name=miraclecast
pkgver=220.2825270
pkgrel=1
#epoch=
pkgdesc="MiracleCast provides software to connect external monitors to your system via Wifi. It is compatible to Miracast. Link-management works, everything else is still being worked on. Replaces openwfd. Contribute on https://github.com/albfan/aur-miraclecast"
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
url="https://github.com/albfan/miraclecast"
license=('GPL')
#groups=()
depends=("systemd>=221")
#makedepends=()
#optdepends=("systemd-kdbus" "kdbus") #kdbus-git provides kdbus
provides=("miraclecast")
#conflicts=()
backup=(etc/dbus-1/system.d/org.freedesktop.miracle.conf)
source=("$_name::git+https://github.com/albfan/miraclecast.git#branch=master")
# generate with 'makepkg -g'
md5sums=('SKIP')

build() {
  cd "$srcdir/$_name"
  ./autogen.sh --prefix=/usr
  ./configure
  make
}

check() {
  cd "$srcdir/$_name"
  make -k check
}

package() {
  cd "$srcdir/$_name"
  make DESTDIR="$pkgdir/" install
}

pkgver() {
  cd "$srcdir/$_name"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}
