pkgname=dni9-dwmblocks
pkgver=1.r5.a414359
pkgrel=1
pkgdesc="My bloated build of dwmblocks"
url="https://github.com/DNI9/dwmblocks"
arch=('any')
license=('GPL3')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft' 'freetype2')
conflicts=('dwmblocks')
provides=("${pkgname}")
options=(!strip !emptydirs)

pkgver() {
  cd "${_pkgname}"
  printf "1.r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cp -af ../source/. ${srcdir}
}

build() {
  cd "$srcdir"
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11 FREETYPEINC=/usr/include/freetype2
}

package() {
  cd "$srcdir"
  make PREFIX=/usr DESTDIR="$pkgdir" install
}
