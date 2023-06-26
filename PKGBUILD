# Maintainer: Danilo J. S. Bellini <danilo dot bellini at gmail dot com>
# Contributor: Angel Velasquez <angvp@archlinux.org>
# Contributor: Jan de Groot <jgc@archlinux.org>
# Contributor: Pellegrion Prevete <pellegrinoprevete@gmail.com>

_py="python2"
_pkg="cairo"
_pkgname="py${_pkg}"
pkgname="${_py}-${_pkg}"
pkgver=1.19.1
pkgrel=2
pkgdesc="Python bindings for the ${_pkg} graphics library"
arch=('x86_64')
url="https://${_pkgname}.readthedocs.io/en/latest/"
license=('LGPL2.1' 'MPL')
depends=("${_pkg}" "${_py}")
provides=("${_pkgname}")
_github="https://github.com/pygobject/${_pkgname}"
source=("${_github}/releases/download/v${pkgver}/${_pkgname}-${pkgver}.tar.gz")
sha256sums=('2c143183280feb67f5beb4e543fd49990c28e7df427301ede04fc550d3562e84')

prepare() {
  cd "${_pkgname}-${pkgver}"
  sed -i 's/raise.*Python 2.*$/pass/' setup.py
}

build() {
  cd "${_pkgname}-${pkgver}"
  "${_py}" setup.py build
}

package() {
  cd "${_pkgname}-$pkgver"
  "${_py}" setup.py install --skip-build \
                            --root="${pkgdir}" \
                            --optimize='1'
}
