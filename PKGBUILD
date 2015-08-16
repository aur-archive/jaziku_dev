# Maintainer: (epsilom) Xavier Corredor <xavier.corredor.llano (a) gmail.com>
pkgname=jaziku_dev
_pkgname=jaziku
pkgver=0.6.0
pkgrel=1
pkgdesc="Jaziku is statistical inference software for the teleconnections analysis"
url="http://hg.ideam.gov.co:8000/meteorologia/jaziku/summary"
arch=('i686' 'x86_64')
license=('GPLv3')
depends=('python2' 'python2-distribute' 'python2-scipy' 'python2-dateutil' 'python2-matplotlib' 'python2-numpy' 'python-imaging' 'python2-clint' 'imagemagick' 'hpgl' 'ncl')
#makedepends=('python2-distribute')
source=("http://dl.dropbox.com/u/3383807/jaziku-$pkgver.tar.gz")
md5sums=('207af6778459963ea0cc1146fbbe3b04')

build() {
	cd ${srcdir}/$_pkgname-$pkgver
	cd bin
	mv jaziku jaziku_dev
	sed -i 's/from jaziku/from jaziku_dev/g' jaziku_dev
	cd ..
	find . -iname '*.py' | xargs sed -i 's/from jaziku/from jaziku_dev/g'
    mv jaziku jaziku_dev
    sed -i 's|"jaziku"|"jaziku_dev"|g' jaziku_dev/env/globals_vars.py
	sed -i 's|bin/jaziku|bin/jaziku_dev|g' setup.py
	sed -i 's|jaziku/|jaziku_dev/|g' MANIFEST.in
	python2 ./setup.py build || return 1
}

package(){
	cd ${srcdir}/$_pkgname-$pkgver
	python2 ./setup.py install --root=$pkgdir || return 1
}
