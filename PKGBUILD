# Maintainer: David J. Haines <djhaines at gmx dot com>
# Contributor: Benjamin Hodgetts (Enverex) <ben@xnode.org>

pkgname=pioneer
pkgver=20150710
pkgrel=1
pkgdesc="A freeform single player space adventure in the spirit of Frontier: Elite II."
arch=('i686' 'x86_64')
url="http://pioneerspacesim.net/"
license=('GPL')
conflicts=('pioneer-git')
install="${pkgname}.install"
depends=('libsigc++' 'libvorbis' 'sdl2_image' 'assimp' 'freetype2')
optdepends=('libtxc_dxtn: may prevent crashes on ATI hardware')

source=("${pkgname}.png"
	"${pkgname}.desktop"
	"${pkgname}.install"
	"https://github.com/pioneerspacesim/${pkgname}/archive/${pkgver}.tar.gz"
	)

md5sums=('46e51941124eb3cf1af9233820223478'
	'3fa2bec38752b70ffff7393ae00dbc71'
	'0078a66710b4aada8afe67975e3e06fe'
	'21f3b4c5176ed8c9d3c5caf118ae8b67'
	)

build () {
    cd "${srcdir}/${pkgname}-${pkgver}"
    ./bootstrap
    PIONEER_DATA_DIR="/usr/share/${pkgname}" ./configure --prefix="/usr"
}

package() {
    install -Dm644 "${srcdir}/${pkgname}.desktop" "${pkgdir}/usr/share/applications/${pkgname}.desktop"
    install -Dm644 "${srcdir}/${pkgname}.png" "${pkgdir}/usr/share/pixmaps/${pkgname}.png"
    install -Dm644 "${srcdir}/${pkgname}-${pkgver}/Quickstart.txt" "${pkgdir}/usr/share/doc/${pkgname}/quickstart.txt"
    cd "${srcdir}/${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" install
}
