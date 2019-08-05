pkgname=st
pkgver=0.8.2
pkgrel=2
pkgdesc='A simple virtual terminal emulator for X.'
arch=('i686' 'x86_64' 'armv7h')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(
  https://dl.suckless.org/st/st-0.8.2.tar.gz
  https://st.suckless.org/patches/nordtheme/st-nordtheme-0.8.2.diff
  https://st.suckless.org/patches/scrollback/st-scrollback-0.8.2.diff
  https://st.suckless.org/patches/scrollback/st-scrollback-mouse-0.8.2.diff
  https://st.suckless.org/patches/vertcenter/st-vertcenter-20180320-6ac8c8a.diff
  config.h
)
sha256sums=(
  'aeb74e10aa11ed364e1bcc635a81a523119093e63befd2f231f8b0705b15bf35'
  'bd7c467dba6027c156d1bd1f3b65d8666787d3c2ff5c743e54e19c6d79a5ba96'
  '9c5aedce2ff191437bdb78aa70894c3c91a47e1be48465286f42d046677fd166'
  '6103a650f62b5d07672eee9e01e3f4062525083da6ba063e139ca7d9fd58a1ba'
  '04e6a4696293f668260b2f54a7240e379dbfabbc209de07bd5d4d57e9f513360'
  'b39227c151fcbdcae84d7331b56dd68d003c590c2d514f224af9e80779d260bf'
)

prepare() {
  cd $srcdir/$pkgname-$pkgver
  patch -i $srcdir/st-nordtheme-0.8.2.diff
  patch -i $srcdir/st-scrollback-0.8.2.diff
  patch -i $srcdir/st-scrollback-mouse-0.8.2.diff
  patch -i $srcdir/st-vertcenter-20180320-6ac8c8a.diff
  cp $srcdir/config.h $srcdir/$pkgname-$pkgver/config.h
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
