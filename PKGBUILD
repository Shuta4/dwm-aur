# Maintainer: Shuta4 <shuta4@proton.me>

pkgname=dwm
pkgver=6.2
pkgrel=1
pkgdesc="A dynamic window manager for X custom build"
url="https://github.com/Shuta4/dwm"
arch=('i686' 'x86_64' 'arm' 'armv7h' 'armv6h' 'aarch64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft' 'freetype2')
source=("dwm.desktop"
        "https://github.com/Shuta4/$pkgname/archive/refs/tags/$pkgver-$pkgrel.tar.gz")
sha256sums=('bc36426772e1471d6dd8c8aed91f288e16949e3463a9933fee6390ee0ccd3f81'
            '18b9a7ab15cf247b888b2f4598521ec1cfd909ceaf2ca7942abb1ee653131845')

prepare() {
  cd "$srcdir/$pkgname-$pkgver-$pkgrel"
}

build() {
  cd "$srcdir/$pkgname-$pkgver-$pkgrel"
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
  cd "$srcdir/$pkgname-$pkgver-$pkgrel"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 README.md "$pkgdir/usr/share/doc/$pkgname/README.md"
  install -Dm644 "$srcdir/dwm.desktop" "$pkgdir/usr/share/xsessions/dwm.desktop"
}
