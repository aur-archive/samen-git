# Maintainer: Kai Uwe Jesussek <kajot@gmx.net>

plugrel=1
pkgname=samen-git
pkgver=20110613
pkgrel=1
pkgdesc="samen is a ultra small wpa_supplicant (wpa_cli) action handler."
arch=('arm' 'i686' 'x86_64')
license=('GPL')
url="http://blog.01232.de"
provides=('samen')
makedepends=('git' 'cmake')
depends=('wpa_supplicant')
optdepends=('dialog: samen-shop text user interface')
_gitroot=("git://github.com/kimperator/Samen.git")
_gitname=("Samen")

build() {
  cd ${srcdir}

 ## Git checkout
  if [ -d ${srcdir}/${_gitname} ] ; then
    msg "Git checkout:  Updating existing tree"
    cd ${_gitname} && git pull origin
    msg "Git checkout:  Tree has been updated"
  else
    msg "Git checkout:  Retrieving sources"
    git clone --depth 1 ${_gitroot}
  fi
  msg "Checkout completed"

 ## Build
  rm -rf ${srcdir}/${_gitname}-build
  cp -r ${srcdir}/${_gitname} ${srcdir}/${_gitname}-build
  cd ${srcdir}/${_gitname}-build
  mkdir build
  cd build
  cmake ..
  make DESTDIR=${pkgdir} install
  cp -r ../additions/arch/etc ${pkgdir}
}
package() {
  true
}
