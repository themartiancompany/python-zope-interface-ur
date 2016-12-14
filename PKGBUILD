# Maintainer : Felix Yan <felixonmars@archlinux.org>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Douglas Soares de Andrade <douglas@archlinux.org>

pkgbase=python-zope-interface
pkgname=('python-zope-interface' 'python2-zope-interface')
pkgver=4.3.3
pkgrel=1
license=('ZPL')
arch=('i686' 'x86_64')
url="http://pypi.python.org/pypi/zope.interface"
makedepends=('python-setuptools' 'python2-setuptools')
checkdepends=('python-zope-event' 'python2-zope-event')
source=("https://pypi.io/packages/source/z/zope.interface/zope.interface-${pkgver}.tar.gz"
        __init__.py)
md5sums=('ba3f32eacaea66094b7e2ae2788cec89'
         '1cdca3de4f8849a3d0d82b678710e112')

prepare() {
  cp -a zope.interface-${pkgver}{,-py2}
}

build() {
  cd "${srcdir}/zope.interface-${pkgver}"
  python setup.py build

  cd "${srcdir}/zope.interface-${pkgver}-py2"
  python2 setup.py build
}

check() {
  cd "${srcdir}/zope.interface-${pkgver}"
  python setup.py test

  cd "${srcdir}/zope.interface-${pkgver}-py2"
  python2 setup.py test
}

package_python-zope-interface() {
  pkgdesc='Zope Interfaces for Python 3.x'
  depends=('python')
 
  cd "${srcdir}/zope.interface-${pkgver}"
  python setup.py install --prefix=/usr --root="${pkgdir}" --optimize=1
  install -Dm644 ../__init__.py "$pkgdir"/usr/lib/python3.5/site-packages/zope/__init__.py
}

package_python2-zope-interface(){
  pkgdesc='Zope Interfaces for Python 2.x'
  depends=('python2')
  replaces=('zope-interface')
  provides=('zope-interface')

  cd "${srcdir}/zope.interface-${pkgver}-py2"
  python2 setup.py install --prefix=/usr --root="${pkgdir}" --optimize=1
  install -Dm644 ../__init__.py "$pkgdir"/usr/lib/python2.7/site-packages/zope/__init__.py
}
