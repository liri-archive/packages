# Maintainer: Pier Luigi Fiorini <pierluigi.fiorini@gmail.com>

pkgname=qt5-gsettings
pkgver=1.1.0
pkgrel=1
pkgdesc="Qt-style wrapper for GSettings"
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
url='https://liri.io'
license=('LGPL3')
depends=('qt5-declarative' 'glib2')
makedepends=('liri-qbs-shared')
groups=('liri')
source=("https://github.com/lirios/qtgsettings/releases/download/v${pkgver}/qtgsettings-${pkgver}.tar.xz")
sha256sums=('9b0de31a77524d66f76f890117306cd6be10a60355b133e6e22cfc4a591ae94a')

build() {
	cd qtgsettings-${pkgver}
	qbs setup-toolchains --type gcc /usr/bin/g++ gcc
	qbs setup-qt /usr/bin/qmake-qt5 qt5
	qbs config profiles.qt5.baseProfile gcc
	qbs build --no-install -d build profile:qt5 qbs.installRoot:/ qbs.installPrefix:usr modules.lirideployment.qmlDir:lib/qt/qml
}

package() {
	cd qtgsettings-${pkgver}
	qbs install -d build --no-build -v --install-root $pkgdir profile:qt5
}
