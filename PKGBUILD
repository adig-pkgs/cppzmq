# Maintainer: Tomasz Jakub Rup <tomasz.rup@gmail.com>
pkgname=cppzmq
pkgver=4.6.0
pkgrel=1
pkgdesc="Header-only C++ binding for libzmq (only CMake module)"
arch=('any')
url="https://github.com/zeromq/cppzmq"
license=('MIT')
makedepends=('cmake')
optdepends=('cmake')
source=("https://github.com/zeromq/cppzmq/archive/v${pkgver}.tar.gz")
md5sums=('7cae1b3fbfeaddb9cf1f70e99a98add2')

prepare() {
	cd "$srcdir/$pkgname-$pkgver"
	mkdir -p build
}

build() {
	cd "$srcdir/$pkgname-$pkgver/build"
	cmake -D CMAKE_INSTALL_PREFIX=/usr -D CPPZMQ_BUILD_TESTS=OFF ..
}

package() {
	depends=('zeromq>=4.2.0')

	cd "$srcdir/$pkgname-$pkgver/build"
	make -j4 DESTDIR="$pkgdir/" install
	cd ..
	rm -rf "$pkgdir/usr/include"
	install -m 755 -d "$pkgdir/usr/share/licenses/$pkgname"
	install -m 644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
