# Maintainer: Thomas Sowell <tom@fancydriving.org>

buildarch=1

pkgname=xf86-video-armsoc
pkgdesc="Open-source X.org graphics driver for TI OMAP graphics"
pkgver=R30.4537
pkgrel=1
arch=('any')
groups=('chromarchy')
url="http://git.chromium.org/gitweb/?p=chromiumos/third_party/xf86-video-armsoc.git;a=summary"
license=('custom')
_gitname='xf86-video-armsoc'
makedepends=('git' 'pkgconfig' 'xorg-server-devel' 'resourceproto' 'scrnsaverproto')

source=(xf86-video-armsoc-compat-X-1-14.patch
        "$_gitname::git+http://git.chromium.org/git/chromiumos/third_party/xf86-video-armsoc#branch=release-R30-4537.B")

md5sums=('29eee72f392a5b02a004dc525875fe37'
         'SKIP')

build() {
  cd "$srcdir/$_gitname"

  git apply "$srcdir/xf86-video-armsoc-compat-X-1-14.patch"

  sh autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  make -C "$srcdir/$_gitname" DESTDIR="$pkgdir/" install

  install -m 644 -D ${srcdir}/${_gitname}/COPYING ${pkgdir}/usr/share/licenses/${pkgname}/COPYING
}
