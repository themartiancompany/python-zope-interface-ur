# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>

pkgbase=python-zope-interface
pkgname=('python-zope-interface' 'python2-zope-interface')
pkgver=4.1.2
pkgrel=2
license=('ZPL')
arch=('i686' 'x86_64')
url="http://pypi.python.org/pypi/zope.interface"
makedepends=('python-setuptools' 'python2-setuptools')
source=("http://pypi.python.org/packages/source/z/zope.interface/zope.interface-${pkgver}.tar.gz")
md5sums=('04298faeaa70b4f3b23fa2ae8987262c')

prepare() {
  cp -a zope.interface-${pkgver}{,-python2}
}

build() {
  #build python3 module
  cd "${srcdir}/zope.interface-${pkgver}"
  python setup.py build

  #build python2 module
  cd "${srcdir}/zope.interface-${pkgver}-python2"
  python2 setup.py build
}

check() {
  cd "${srcdir}/zope.interface-${pkgver}"
  python setup.py test

  cd "${srcdir}/zope.interface-${pkgver}-python2"
  python2 setup.py test
}

package_python-zope-interface() {
  pkgdesc=('Zope Interfaces for Python 3.x')
  depends=('python')
 
  cd "${srcdir}/zope.interface-${pkgver}"
  python setup.py install --prefix=/usr --root="${pkgdir}" --optimize=1
  cp src/zope/__init__.py "${pkgdir}/usr/lib/python3.4/site-packages/zope/"
}

package_python2-zope-interface(){
  pkgdesc=('Zope Interfaces for Python 2.x')
  depends=('python2')
  replaces=('zope-interface')
  provides=('zope-interface')

  cd "${srcdir}/zope.interface-${pkgver}-python2"
  python2 setup.py install --prefix=/usr --root="${pkgdir}" --optimize=1
  cp src/zope/__init__.py "${pkgdir}/usr/lib/python2.7/site-packages/zope/"
}
