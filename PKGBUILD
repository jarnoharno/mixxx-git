# Maintainer: Gimmeapill <gimmeapill at gmail dot com>

pkgname=mixxx-git
pkgver=release.1.12.0.beta1.r1566.g4cc07d8
pkgrel=1
pkgdesc="Digital DJ mixing software. Development branch from git with cpu optimization enabled"
arch=('i686' 'x86_64')
url='http://www.mixxx.org/'
license=('GPL2')
depends=('libid3tag' 'libmad' 'portaudio' 'qt4' 'libshout' 'taglib' 'portmidi'
    'protobuf' 'fftw' 'libusbx' 'chromaprint' 'rubberband' 'faad2' 'libmp4v2'
    'libogg' 'libvorbis')
makedepends=('git' 'scons' 'pkgconfig' 'glu')
conflicts=('mixxx' 'mixxx-bzr' 'mixxx1.10-bzr' 'mixxx1.11-bzr' 'mixxx-beta'
    'mixxx1.11-git' 'mixxx1.12-git' 'mixxxold' 'mixxx-aac')
provides=('mixxx')
_gitname=mixxx
source=("git+https://github.com/mixxxdj/${_gitname}")
md5sums=('SKIP')

pkgver() {
  cd "${srcdir}/${_gitname}"
  echo "$(git describe --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g')"
}

build() {
  cd "${srcdir}/${_gitname}"
  scons -j $(nproc) qtdir=/usr/lib/qt4 prefix=/usr \
      optimize=native install_root="${pkgdir}/usr" faad=1
}

package() {
  cd "${srcdir}/${_gitname}"
  scons -j $(nproc) qtdir=/usr/lib/qt4 prefix=/usr \
      install_root="${pkgdir}/usr" install
}

