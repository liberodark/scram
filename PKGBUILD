# Maintainer: liberodark

pkgname=scram
pkgver=0.15.0
pkgrel=1
pkgdesc='Probabilistic risk analysis tool'
arch=('x86_64')
url='https://scram-pra.org/'
license=('GPL3')
depends=('boost-libs' 'gperftools' 'libxml++2.6')
makedepends=('boost' 'cmake')
source=("$pkgname-$pkgver.tar.gz::https://github.com/rakhimov/scram/archive/$pkgver.tar.gz")
sha512sums=('a7401a6c8f44715cb2658ef57f6f10b15790444f2c53f44323ca6f42c08f481b05a840e1485df4866e0ea89c37291e8a4d9f47021d712b7177e5919e231f8c63')

build() {
  cd $pkgname-$pkgver
  mkdir -p build && cd build
  cmake .. \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_BUILD_TYPE=Release \
    -DBUILD_GUI=OFF \
    -DBUILD_TESTS=OFF \
    -DBUILD_SHARED_LIBS=OFF \
    -DINSTALL_LIBS=OFF
  make
}

package() {
  cd $pkgname-$pkgver
  make -C build DESTDIR="$pkgdir" install
  install -p -D -m 644 doc/scram.h2m -t "$pkgdir/usr/share/man/man1/"
  install -p -D -m 644 scripts/scram "$pkgdir/usr/share/bash-completion/completions/scram"
}
