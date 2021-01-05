pkgname=st
pkgver=0.8.4
pkgrel=2
pkgdesc='A simple virtual terminal emulator for X.'
arch=('i686' 'x86_64' 'armv7h')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(
  https://dl.suckless.org/st/st-0.8.4.tar.gz
  https://st.suckless.org/patches/nordtheme/st-nordtheme-0.8.2.diff
  https://st.suckless.org/patches/scrollback/st-scrollback-0.8.4.diff
  https://st.suckless.org/patches/vertcenter/st-vertcenter-20180320-6ac8c8a.diff
  https://st.suckless.org/patches/anysize/st-anysize-0.8.1.diff
  my-config.diff
)
sha256sums=(
  'd42d3ceceb4d6a65e32e90a5336e3d446db612c3fbd9ebc1780bc6c9a03346a6'
  '01de8a6d0d855c31496c7963e78edb7565a81b60dcb9e9f00dd3eab1f43b526b'
  '418e1c5df11105482f13a008218c89eadb974630c25b4a6ff3da763dc2560e44'
  '04e6a4696293f668260b2f54a7240e379dbfabbc209de07bd5d4d57e9f513360'
  '8118dbc50d2fe07ae10958c65366476d5992684a87a431f7ee772e27d5dee50f'
  'SKIP'
)


prepare() {
  cd $srcdir/$pkgname-$pkgver
  patch -i $srcdir/st-nordtheme-0.8.2.diff
  patch -i $srcdir/st-scrollback-0.8.4.diff
  patch -i $srcdir/st-vertcenter-20180320-6ac8c8a.diff
  patch -i $srcdir/st-anysize-0.8.1.diff
  patch -i $srcdir/my-config.diff
}

build() {
  cd $srcdir/$pkgname-$pkgver
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 README "$pkgdir/usr/share/doc/$pkgname/README"
  # remove to avoid conflict with ncurses
  rm "${pkgdir}/usr/share/terminfo/s/st" "${pkgdir}/usr/share/terminfo/s/st-256color"
}
