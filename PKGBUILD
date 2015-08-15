# Maintainer: Milan Oberkirch <aur@oberkirch.org>

__upstream_name=flite
pkgname=${__upstream_name}-full
pkgver=1.4
pkgrel=3
pkgdesc="A lighweight version of festival speech synthesis compiled with shared libs."
arch=('i686' 'x86_64')
url="http://www.speech.cs.cmu.edu/flite/"
license=('custom')
depends=('glibc')
provides=('flite=$pkgver')
conflicts=('flite')
source=("http://www.speech.cs.cmu.edu/flite/packed/${__upstream_name}-${pkgver}/${__upstream_name}-${pkgver}-release.tar.bz2" shared_lib_fix.patch)
md5sums=('b7c3523b3bbc6f29ce61e6650cd9a428'
         'ebf5435d16d67ba7bca05975fa46970d')

build() {
  cd "${srcdir}/${__upstream_name}-${pkgver}-release"
  patch config/common_make_rules "${srcdir}/shared_lib_fix.patch"
  ./configure --prefix=/usr --enable-shared || return 1
  make || return 1
}

package() {
  cd "${srcdir}/${__upstream_name}-${pkgver}-release"
  make prefix="${pkgdir}/usr" install || return 1
  install -D -m644 COPYING "${pkgdir}/usr/share/licenses/${__upstream_name}/LICENSE" || return 1
}
