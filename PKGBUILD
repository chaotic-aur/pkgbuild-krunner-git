# Merged with official ABS krunner PKGBUILD by João, 2021/02/01 (all respective contributors apply herein)
# Maintainer: João Figueiredo & chaotic-aur <islandc0der@chaotic.cx>
# Contributor: Felix Golatofski <contact@xdfr.de>
# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Antonio Rojas <arojas@archlinux.org>

pkgname=krunner-git
pkgver=5.83.0_r627.gf60ec40
pkgrel=1
pkgdesc='Framework for providing different actions given a string query'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
groups=(kf5-git)
depends=(plasma-framework-git threadweaver-git)
makedepends=(git extra-cmake-modules-git kdoctools-git doxygen qt5-tools)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
