# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Antonio Rojas <arojas@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

#_commit=4206046f12b7f029ff95c6fda4fd5bfc81564131
pkgname=kwin
pkgver=5.23.4.r20499.g0db88c3ea
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
#source=("git+https://github.com/KDE/$pkgname.git#commit=$_commit")
source=("git+https://github.com/KDE/$pkgname.git")
install=$pkgname.install
sha256sums=('SKIP')

pkgver() {
  cd $pkgname
  _ver=5.23.4
  echo "${_ver}.r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S $pkgname \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

