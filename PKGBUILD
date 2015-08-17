pkgname=starcheat-git
pkgver=167
pkgrel=1
pkgdesc="Starbound player save editor and Python library"
arch=(any)
url="http://community.playstarbound.com/index.php?resources/starcheat.699/"
license=("MIT")
depends=(python-pyqt5)
makedepends=(git python)
conflicts=(starcheat)
provides=(starcheat)
source=("${pkgname%-*}::git+https://github.com/wizzomafizzo/starcheat.git"
"starcheat.png"
"starcheat.desktop"
"starcheat.sh")
md5sums=('SKIP'
         'fef910a20b891667d9907343c6221ba8'
         'ef05183a35e289f6e036068db0d8c30b'
         'b1bdefdf82633ee135ea8980304f5513')

pkgver () {
	cd "$srcdir/${pkgname%-*}"
	echo $(git rev-list --count master)
}

build() {
	cd "${srcdir}/${pkgname%-*}"
	./build.sh
}

package() {
	cd "${srcdir}/${pkgname%-*}"
	install -Dm755 "$srcdir/starcheat.sh" "$pkgdir/usr/bin/starcheat"
	install -Dm644 "$srcdir/starcheat.png" "$pkgdir/usr/share/icons/starcheat.png"
	install -Dm644 LICENSE.txt "$pkgdir/usr/share/licenses/starcheat/LICENSE.txt"
	install -Dm644 "$srcdir/starcheat.desktop" "$pkgdir/usr/share/applications/starcheat.desktop"
	cd build
	find . -name '*.py' -exec install -Dm644 {} "$pkgdir/usr/share/starcheat/"{} \;
	python -m compileall "$pkgdir/usr/share/starcheat"
} 
