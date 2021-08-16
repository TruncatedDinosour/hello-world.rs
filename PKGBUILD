pkgname='hello-world-git'
_pkgname='hello-world.rs'
pkgver=0.1.0.r88.3d04247
pkgrel=1
arch=('x86_64' 'i686')
url="https://github.com/mTvare6/hello-world.rs"
pkgdesc="Memory safe, blazing fast, configurable, minimal hello world written in rust under 1 line of code with few dependencies"
license=('custom')
makedepends=(rust cargo git)
depends=(cairo gtk3 alsa-lib glfw-x11 freetype2 glib2 pango atk gdk-pixbuf2)
provides=('hello-world')
conflicts=('hello-world')
source=("git://github.com/mTvare6/hello-world.rs")
sha256sums=('SKIP')

pkgver() {
	cd "$_pkgname"
	echo "$(awk '/^VERSION =/ {print $3}' config.mk)".r"$(git rev-list --count HEAD)"."$(git rev-parse --short HEAD)"
}

build() {
	cd "$_pkgname"
	make
}

package() {
	cd "$_pkgname"
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
# vim:set ts=4 sw=4 noet: