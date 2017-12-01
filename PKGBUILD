# Maintainer: Christian Vogel <vogelchr@vogel.cx>

pkgname=soapy-uhd
pkgver=0.0
pkgrel=1
epoch=1
pkgdesc="Soapy SDR plugins for UHD devices"
arch=('any')
url="https://github.com/pothosware/SoapyUHD"
license=('GPL V3')
provides=('soapyuhd')
conflicts=()
makedepends=('git' 'cmake')
depends=('boost' 'boost-libs' 'soapysdr' 'libuhd')
optdepends=() 
source=(${pkgname}::"git+https://github.com/pothosware/SoapyUHD.git")
sha256sums=('SKIP')

pkgver() {
  cd "$pkgname"
  git describe --long | sed 's/^soapy-uhd-//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
	cd "${srcdir}/${pkgname}"
	mkdir -p build
	cd build
	cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr
	make 
}

package() {
	make -C "${srcdir}/${pkgname}/build" DESTDIR="${pkgdir}" install
}
