## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=qt5-lipstick-glacier-home-git
_host="gitlab.com"
_srcname=qt5-lipstick-glacier-home
_project=neochapay # github nemomobile-ux/glacier-home fork
_branch=Qt59
pkgver=r267.8a72bc1
pkgrel=1
pkgdesc="A nice homescreen for Glacier experience"
arch=('x86_64' 'aarch64')
url="https://$_host/$_project/glacier-home#branch=$_branch"
license=('BSD')
depends=('qt5-base' 'nemo-qml-plugin-contextkit-git' 'libconnman-qt-git')
makedepends=('git' 'qt5-lipstick-git') #TODO
optdepends=()
provides=("${_srcname}")
conflicts=()
source=("${pkgname}::git+${url}")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/${pkgname}"
  ( set -o pipefail
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  ) 2>/dev/null
}

build() {
  cd "${srcdir}/${pkgname}"
  mkdir -p build
  cd build
  qmake ..
  make
}

package() {
  cd "${srcdir}/${pkgname}"
  cd build
  make INSTALL_ROOT="${pkgdir}" install
}
 
