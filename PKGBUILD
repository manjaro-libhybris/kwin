# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kwin
pkgver=5.22.3.r19687.gca301d191
pkgrel=1
pkgdesc='An easy to use, but flexible, composited Window Manager'
arch=(x86_64 aarch64)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
replaces=($pkgname-git)
depends=(kscreenlocker xcb-util-cursor plasma-framework kcmutils kwayland-server breeze
         qt5-script pipewire libqaccessibilityclient lcms2)
makedepends=(git extra-cmake-modules qt5-tools kdoctools krunner)
optdepends=('qt5-virtualkeyboard: virtual keyboard support for kwin-wayland')
groups=(plasma)
source=("git+https://github.com/KDE/$pkgname.git")
install=$pkgname.install
sha256sums=('SKIP')
validpgpkeys=('2D1D5B0588357787DE9EE225EC94D18F7F05997E'  # Jonathan Riddell <jr@jriddell.org>
              '0AAC775BB6437A8D9AF7A3ACFE0784117FBCE11D'  # Bhushan Shah <bshah@kde.org>
              'D07BD8662C56CB291B316EB2F5675605C74E02CF'  # David Edmundson <davidedmundson@kde.org>
              '1FA881591C26B276D7A5518EEAAF29B42A678C20') # Marco Martin <notmart@gmail.com>

build() {
  cmake -B build -S $pkgname \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

pkgver() {
  cd $pkgname
  _ver=5.22.3
  echo "${_ver}.r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}
