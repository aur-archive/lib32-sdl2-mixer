#Maintainer: Jameson Pugh <imntreal@gmail.com>

pkgname=lib32-sdl2-mixer
pkgver=2.0.0
pkgrel=3
pkgdesc="SDL2 mixer libraries"
arch=('i686' 'x86_64')
url="http://www.libsdl.org"
license=('MIT')
depends=('lib32-sdl2' 'lib32-libmodplug')
optdepends=(lib32-libvorbis lib32-flac lib32-fluidsynth lib32-libmikmod)
provides=(lib32-sdl2_mixer)
options=(!libtool)
source=("http://www.libsdl.org/projects/SDL_mixer/release/SDL2_mixer-${pkgver}.tar.gz")
sha256sums=('a8ce0e161793791adeff258ca6214267fdd41b3c073d2581cd5265c8646f725b')

build() {
  export CC='gcc -m32'
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH='/usr/lib32/pkgconfig'

  cd "${srcdir}/SDL2_mixer-${pkgver}/"
  ./configure --disable-static --prefix=/usr --libdir=/usr/lib32
  make
}

package() {
  cd "${srcdir}/SDL2_mixer-${pkgver}/"
  make DESTDIR="${pkgdir}" install
  install -Dm644 COPYING.txt "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
  rm -rf "$pkgdir/usr/share/aclocal/" "$pkgdir/usr/include/" "${pkgdir}/usr/bin/"
}
## vim:set ts=2 sw=2 et:
