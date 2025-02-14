# Maintainer: Petr Kracik <petrkr@petrkr.net>

pkgname=freedata-gui
pkgver=0.16.9
pkgrel=1
pkgdesc="GUI for FreeDATA. A versatile, open-source platform designed specifically for HF communications, leveraging Codec2 data modes for robust global digital communication. It features a network-based server-client architecture, a REST API, multi-platform compatibility, and a messaging system."
arch=('x86_64')
url="https://wiki.freedata.app"
license=('GPL-3.0')
depends=('freedata-server')
makedepends=()

source=("https://github.com/DJ2LS/FreeDATA/archive/refs/tags/v${pkgver}.tar.gz")

sha256sums=('962b393492fd158acf7d41d9211aa24409b98fe1fb0b96ae89e9b919d583d711')

build() {
	cd "${srcdir}"
	cd FreeDATA-${pkgver}/freedata_gui
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
	cp -a ${srcdir}/FreeDATA-${pkgver}/freedata_gui/dist ./freedata_gui/dist/

	# Copy License and documentation
	cp ${srcdir}/FreeDATA-${pkgver}/LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/
	cp -a ${srcdir}/FreeDATA-${pkgver}/documentation ${pkgdir}/usr/share/doc/${pkgname}
}
