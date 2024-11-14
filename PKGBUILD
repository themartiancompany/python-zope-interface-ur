# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=zope-interface
_Pkg=zope.interface
_pkgname="${_pkg}"
pkgname="${_py}-${_pkg}"
pkgver=6.1
pkgrel=1
license=(
  'ZPL'
)
arch=(
 'x86_64'
 'arm'
 'aarch64'
 'i686'
 'pentium4'
 'mips'
)
url="https://pypi.python.org/pypi/${_Pkg}"
pkgdesc='Zope Interfaces for Python 3.x'
depends=(
  "${_py}-setuptools"
)
checkdepends=(
  "${_py}-zope-event"
  "${_py}-zope-testing"
)
_pypi="https://pypi.io/packages/source"
source=(
  "${_pypi}/${_pkg::1}/${_Pkg}/${_Pkg}-${pkgver}.tar.gz"
)
sha512sums=(
  '04305eaf98fb40269d417c6894a6e154340669b66033c50e130d58bf6166cabc0a8979e1ba80dda47cb2bc508dde01ea2175628f89cbfd44cc2f59ac3cdce2c0'
)

prepare() {
  cd \
    "${_Pkg}-${pkgver}"
  sed \
    -i \
      '/coverage/d' \
    setup.py
}

build() {
  cd \
    "${_Pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      build
}

check() {
  cd \
    "${_Pkg}-${pkgver}"
  PYTHONPATH="$PWD/build/lib.linux-$CARCH-cpython-311" \
  python \
    setup.py \
      test
}

package() {
  cd \
    "${_Pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      install \
      --prefix=/usr \
      --root "${pkgdir}" \
      --optimize=1
}

# vim:set sw=2 sts=-1 et:
