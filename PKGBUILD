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
  https://st.suckless.org/patches/anysize/st-anysize-0.8.1.diff
  config.h
)
sha256sums=(
  'aeb74e10aa11ed364e1bcc635a81a523119093e63befd2f231f8b0705b15bf35'
  '01de8a6d0d855c31496c7963e78edb7565a81b60dcb9e9f00dd3eab1f43b526b'
  '9c5aedce2ff191437bdb78aa70894c3c91a47e1be48465286f42d046677fd166'
  '6103a650f62b5d07672eee9e01e3f4062525083da6ba063e139ca7d9fd58a1ba'
  '04e6a4696293f668260b2f54a7240e379dbfabbc209de07bd5d4d57e9f513360'
  '8118dbc50d2fe07ae10958c65366476d5992684a87a431f7ee772e27d5dee50f'
  '3b241e683870973b543668cd5f3948806c32d58c203548d72273c69273d4260d'
)

prepare() {
  cd $srcdir/$pkgname-$pkgver
  patch -i $srcdir/st-nordtheme-0.8.2.diff
  patch -i $srcdir/st-scrollback-0.8.2.diff
  patch -i $srcdir/st-scrollback-mouse-0.8.2.diff
  patch -i $srcdir/st-vertcenter-20180320-6ac8c8a.diff
  patch -i $srcdir/st-anysize-0.8.1.diff
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
