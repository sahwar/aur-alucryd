# Maintainer: Maxime Gauduin <alucryd@archlinux.org>

pkgname=pantheon-applications-menu-git
pkgver=2.4.2.r11.eb95a41
pkgrel=1
pkgdesc='The Pantheon Application Menu'
arch=(x86_64)
url=https://github.com/elementary/applications-menu
license=(GPL3)
groups=(pantheon-unstable)
depends=(
  appstream
  gdk-pixbuf2
  glib2
  gnome-menus
  gtk3
  json-glib
  libgee
  libgranite.so
  libsoup
  libswitchboard-2.0.so
  libwingpanel-2.0.so
  zeitgeist
)
makedepends=(
  git
  meson
  granite-git
  switchboard-git
  vala
  wingpanel-git
)
provides=(pantheon-applications-menu)
conflicts=(pantheon-applications-menu)
#source=(pantheon-applications-menu::git+https://github.com/elementary/applications-menu.git)
source=(pantheon-applications-menu::git+https://github.com/alucryd/applications-menu.git#branch=meson-plank)
sha256sums=(SKIP)

pkgver() {
  cd pantheon-applications-menu

  git describe --tags | sed 's/-/.r/; s/-g/./'
}

build() {
  arch-meson pantheon-applications-menu build \
    -D b_pie=false \
    -D with-unity=false
  ninja -C build
}

package() {
  DESTDIR="${pkgdir}" meson install -C build
}

# vim: ts=2 sw=2 et:
