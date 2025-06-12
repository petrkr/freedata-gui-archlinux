# Maintainer: Petr Kracik <petrkr@petrkr.net>

pkgname=freedata-gui
pkgver=0.17.3
pkgrel=1
pkgdesc="GUI for FreeDATA. A versatile, open-source platform designed specifically for HF communications, leveraging Codec2 data modes for robust global digital communication. It features a network-based server-client architecture, a REST API, multi-platform compatibility, and a messaging system."
arch=('x86_64')
url="https://wiki.freedata.app"
license=('GPL-3.0')
depends=('freedata-server')
makedepends=('npm')

source=("https://github.com/DJ2LS/FreeDATA/archive/refs/tags/v${pkgver}-beta.tar.gz")

sha256sums=('322d31d10d4a8e676769ebdfcb78004916de35f020ff56b96d1d2c0ddd7fddbc')

build() {
	cd "${srcdir}"
	cd FreeDATA-${pkgver}-beta/freedata_gui
	npm install
	npm run build 
}

package() {
	cd ${pkgdir}
	mkdir -p "opt/FreeDATA"
	mkdir -p "opt/FreeDATA/freedata_gui" 
	mkdir -p "usr/share/doc"
	mkdir -p "usr/share/licenses/${pkgname}"

	cd ${pkgdir}/opt/FreeDATA
		
	# Copy GUI
	cp -a ${srcdir}/FreeDATA-${pkgver}-beta/freedata_gui/dist ./freedata_gui/dist/

	# Copy License and documentation
	cp ${srcdir}/FreeDATA-${pkgver}-beta/LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/
	cp -a ${srcdir}/FreeDATA-${pkgver}-beta/documentation ${pkgdir}/usr/share/doc/${pkgname}
}
