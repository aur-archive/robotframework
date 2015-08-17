# Contributor: Thomas Robinson <robinsthom@gmail.com>
pkgname=robotframework
pkgver=2.8.4
pkgrel=1
pkgdesc="A keyword-driven test automation framework"
arch=('i686' 'x86_64')
url="http://www.robotframework.org"
license=('APACHE')
depends=('python2')
optdepends=('jython: for using robotframework with Java (must be installed before running PKGBUILD)')
source=("https://pypi.python.org/packages/source/r/robotframework/$pkgname-$pkgver.tar.gz")
md5sums=('bdc08d5667ed5860ba674745660ef72b')

package() {
    cd "$srcdir/$pkgname-$pkgver"

    echo "creating pybot scripts"
    python2 setup.py install --prefix=/usr --root="$pkgdir" || return 1 

    if pacman -Qsq ^jython$;
    then
        echo "creating jybot scripts"
        jython setup.py install --prefix=/opt/jython --root="$pkgdir" || return 1 
        mv $pkgdir/opt/jython/bin/* $pkgdir/usr/bin/
    fi
}
