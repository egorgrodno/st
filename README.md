# st - simple terminal

[st](https://st.suckless.org/ 'st') is a simple terminal emulator for X which sucks less.

## Requirements

In order to build st you need the Xlib header files.

## Patches

* st-dracula-0.8.diff
  * Dracula theme
  * Based on [st-dracula-20170803-7f99032.diff](https://st.suckless.org/patches/dracula/ 'st-dracula-20170803-7f99032.diff'), adjusted for v0.8
* st-font-source-code-pro-nerd-0.8.diff
  * [Source Code Pro Nerd Font](https://aur.archlinux.org/packages/nerd-fonts-source-code-pro/ 'Source Code Pro Nerd Font')
* st-scrollback-0.8.diff
  * Scroll back through terminal output using Shift+{PageUp, PageDown}.
  * Based on [st-scrollback-0.8.diff](https://st.suckless.org/patches/scrollback/ 'st-scrollback-0.8.diff'), adjusted scroll size (5 lines instead of 1 page)

## Installation

Apply the patches you need:

    git apply patches/*.diff

Edit config.mk to match your local setup (st is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install st (if
necessary as root):

    make clean install

## Credits

Based on Aurélien APTEL bt source code.
