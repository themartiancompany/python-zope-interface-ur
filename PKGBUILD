# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>

pkgbase=python-zope-interface
pkgname=('python-zope-interface' 'python2-zope-interface')
pkgver=4.4.2
pkgrel=1
license=('ZPL')
arch=('i686' 'x86_64')
url="http://pypi.python.org/pypi/zope.interface"
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-zope-event' 'python2-zope-event')
source=("https://pypi.io/packages/source/z/zope.interface/zope.interface-$pkgver.tar.gz")
sha512sums=('11b95cf358e3151860a0f8a5d3d151cc4dad582aea39b5268e67b683f14343938b66315051d0ffae48d1890ec4c4a0dfcb16de912aae5fcb78ab128668735c2a')

prepare() {
  cp -a zope.interface-${pkgver}{,-py2}
}

build() {
  cd "$srcdir"/zope.interface-$pkgver
  python setup.py build

  cd "$srcdir"/zope.interface-$pkgver-py2
  python2 setup.py build
}

check() {
  cd "$srcdir"/zope.interface-$pkgver
  python setup.py test

  cd "$srcdir"/zope.interface-$pkgver-py2
  python2 setup.py test
}

package_python-zope-interface() {
  pkgdesc='Zope Interfaces for Python 3.x'
  depends=('python')
 
  cd zope.interface-$pkgver
  python setup.py install --prefix=/usr --root="$pkgdir" --optimize=1
}

package_python2-zope-interface(){
  pkgdesc='Zope Interfaces for Python 2.x'
  depends=('python2')

  cd zope.interface-$pkgver-py2
  python2 setup.py install --prefix=/usr --root="$pkgdir" --optimize=1
}
