# Maintainer: Petr Kracik <petrkr@petrkr.net>

pkgname=freedata-gui
pkgver=0.16.11
pkgrel=1
pkgdesc="GUI for FreeDATA. A versatile, open-source platform designed specifically for HF communications, leveraging Codec2 data modes for robust global digital communication. It features a network-based server-client architecture, a REST API, multi-platform compatibility, and a messaging system."
arch=('x86_64')
url="https://wiki.freedata.app"
license=('GPL-3.0')
depends=('freedata-server')
makedepends=('npm')

source=("https://github.com/DJ2LS/FreeDATA/archive/refs/tags/v${pkgver}.tar.gz")

sha256sums=('f7485e5bd45cd3fa99205bfde6f36314fddb1d7f566fde62da09a609f394272b')

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
