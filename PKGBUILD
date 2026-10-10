# Maintainer : Will Elliott <troutcobbler@gmail.com>

pkgname=euro-office-bin
pkgver=9.3.5
pkgrel=2
pkgdesc='An office suite that combines text, spreadsheet and presentation editors'
arch=('x86_64')
url='https://www.onlyoffice.com/'
license=('AGPL-3.0-only')
depends=(
    'alsa-lib'
    'at-spi2-core'
    'cairo'
    'curl'
    'dbus'
    'desktop-file-utils'
    'expat'
    'fontconfig'
    'freetype2'
    'glib2'
    'glibc'
    'gtk3'
    'gstreamer'
    'gst-plugins-base-libs'
    'gst-plugins-ugly'
    'hicolor-icon-theme'
    'libcups'
    'libdrm'
    'libgcc'
    'libgl'
    'libnotify'
    'libpulse'
    'libstdc++'
    'libx11'
    'libxcomposite'
    'libxdamage'
    'libxcb'
    'libxext'
    'libxfixes'
    'libxi'
    'libxkbcommon'
    'libxrandr'
    'libxss'
    'mesa'
    'nss'
    'nspr'
    'pango'
    'sh'
    'ttf-carlito'
    'ttf-dejavu'
    'ttf-liberation')
optdepends=(
    'gst-libav: for playing embedded video files'
    'gst-plugins-good: for playing embedded video files'
    'libreoffice: for OpenSymbol fonts'
    'otf-takao: for japanese Takao fonts'
    'ttf-ms-fonts: for Microsoft fonts')
provides=("euro-office=${pkgver}")
conflicts=('onlyoffice')
options=('!debug' '!emptydirs' '!strip')
source=("euro-office-euro-office_${pkgver}-${pkgrel}_${CARCH}.deb"::"https://github.com/Euro-Office/DesktopEditors/releases/download/v${pkgver}-${pkgrel}/euro-office-euro-office_${pkgver}-${pkgrel}_amd64.deb"
        '010-euro-office-bin-fix-document-opening.patch')
noextract=("euro-office-euro-office_${pkgver}-${pkgrel}_${CARCH}.deb")
sha256sums=('d1e9287bfb9278f69ca729e5df3d1dd260f58a2672f506a2efa64a4bb025e5a4'
            '52ca85b7f991920e97b437e40320d89110ddf7dd1e748d2f7cfb504c0c9bf824')

prepare() {
    mkdir -p "euro-office-${pkgver}-${pkgrel}/pkg"
    bsdtar -xf "${srcdir}/euro-office-euro-office_${pkgver}-${pkgrel}_${CARCH}.deb" -C "euro-office-${pkgver}-${pkgrel}"
    bsdtar -xf "euro-office-${pkgver}-${pkgrel}/data.tar.xz" -C "euro-office-${pkgver}-${pkgrel}/pkg"
    patch -d "euro-office-${pkgver}-${pkgrel}/pkg" -Np1 -i "${srcdir}/010-euro-office-bin-fix-document-opening.patch"
}

package() {
    cp -dr --no-preserve='ownership' "euro-office-${pkgver}-${pkgrel}"/pkg/* "$pkgdir"
}
