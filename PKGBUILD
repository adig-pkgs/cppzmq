# Maintainer: Tomasz Jakub Rup <tomasz.rup@gmail.com>
pkgname=cppzmq
pkgver=4.7.1
pkgrel=1
pkgdesc="Header-only C++ binding for libzmq (only CMake module)"
arch=('any')
url="https://github.com/zeromq/cppzmq"
license=('MIT')
makedepends=('cmake')
optdepends=('cmake')
source=("https://github.com/zeromq/cppzmq/archive/v${pkgver}.tar.gz")
md5sums=('e85cf23b5aed263c2c5c89657737d107')

build() {
	cd "$srcdir/$pkgname-$pkgver"
	cmake -D CMAKE_INSTALL_PREFIX=/usr -D CPPZMQ_BUILD_TESTS=OFF -B build
	cmake --build build -j$(nproc)
}

package() {
	depends=('zeromq>=4.2.0')

	cd "$srcdir/$pkgname-$pkgver/build"
	DESTDIR="$pkgdir/ " cmake --install .
	cd ..
	rm -rf "$pkgdir/usr/include"
	install -m 755 -d "$pkgdir/usr/share/licenses/$pkgname"
	install -m 644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
