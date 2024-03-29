# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

pkgname=python-zope-interface
pkgver=6.1
pkgrel=1
license=('ZPL')
arch=(
 'x86_64'
 'arm'
 'aarch64'
 'i686'
 'pentium4'
)
url="https://pypi.python.org/pypi/zope.interface"
pkgdesc='Zope Interfaces for Python 3.x'
depends=(
  'python-setuptools'
)
checkdepends=(
  'python-zope-event'
  'python-zope-testing')
source=("https://pypi.io/packages/source/z/zope.interface/zope.interface-$pkgver.tar.gz")
sha512sums=('04305eaf98fb40269d417c6894a6e154340669b66033c50e130d58bf6166cabc0a8979e1ba80dda47cb2bc508dde01ea2175628f89cbfd44cc2f59ac3cdce2c0')

prepare() {
  cd zope.interface-$pkgver
  sed -i '/coverage/d' setup.py
}

build() {
  cd zope.interface-$pkgver
  python setup.py build
}

check() {
  cd zope.interface-$pkgver
  PYTHONPATH="$PWD/build/lib.linux-$CARCH-cpython-311" python setup.py test
}

package() {
  cd zope.interface-$pkgver
  python \
    setup.py \
      install \
      --prefix=/usr \
      --root "${pkgdir}" \
      --optimize=1
}

# vim:set sw=2 sts=-1 et:
