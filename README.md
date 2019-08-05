# st - simple terminal

This is a patched and preconfigured [st](https://st.suckless.org/ 'st') package.

## Applied patches

* [nordtheme](https://st.suckless.org/patches/nordtheme/)
* [scrollback](https://st.suckless.org/patches/scrollback/)
* [vertcenter](https://st.suckless.org/patches/vertcenter/)

## Configuration

To configure the package edit [config.h](config.h) file.

## Installation

    $ ./install.sh

That simple script will install package using [makepkg](https://wiki.archlinux.org/index.php/Makepkg 'makepkg') and cleanup afterwards. All the build information can be found in [PKGBUILD](PKGBUILD) and information about `PKGBUILD` can be found [here](https://wiki.archlinux.org/index.php/PKGBUILD 'pkgbuild').

## Credits

Based on Aurélien APTEL bt source code.
