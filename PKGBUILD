# Maintainer: MicLeh <micleh at proton dot me>
pkgname=doublecmd-qt6-bin
_pkgname=doublecmd
pkgver=1.2.8
pkgrel=3
pkgdesc="Twin-panel (commander-style) file manager (Qt6, prebuilt binary)"
arch=('x86_64')
url="https://doublecmd.sourceforge.io/"
license=('GPL-2.0-or-later' 'LGPL-2.0-or-later' 'MIT' 'MPL-1.1' 'MPL-2.0' 'Apache-2.0' 'BSD-2-Clause' 'Zlib')
options=('!strip' '!debug')
depends=(
    'qt6-base'
    'libb2'
    'liburing'
    'md4c'
    'brotli'
    'zstd'
    'double-conversion'
    'icu'
    'pcre2'
    'glib2'
    'harfbuzz'
    'graphite'
    'fontconfig'
    'freetype2'
    'libpng'
    'libglvnd'
    'libx11'
    'libxcb'
    'libxkbcommon'
    'systemd-libs'
    'wayland'
    'dbus'
    'gcc-libs'
    'desktop-file-utils'
    'hicolor-icon-theme'
    'shared-mime-info'
)
optdepends=(
    'lua: scripting'
    'unzip: support extracting zip archives'
    'zip: support packing zip archives'
    'p7zip: support for 7zip archives'
    'libunrar: support for rar archives'
    'imagemagick: preview xcf files'
    'ffmpegthumbnailer: preview video files'
    'mplayer: to make use of the wlxmplayer plugin'
)
provides=("$_pkgname")
replaces=('doublecmd-qt' 'doublecmd-qt4' 'doublecmd-gtk' 'doublecmd-gtk2')
conflicts=('doublecmd-qt5' 'doublecmd-gtk' 'doublecmd-gtk2')
source=(
    "https://github.com/${_pkgname}/${_pkgname}/releases/download/v${pkgver}/${_pkgname}-${pkgver}.qt6.x86_64.tar.xz"
    "https://raw.githubusercontent.com/${_pkgname}/${_pkgname}/v${pkgver}/install/linux/doublecmd.desktop"
    "https://raw.githubusercontent.com/${_pkgname}/${_pkgname}/v${pkgver}/install/linux/doublecmd.1"
    "https://raw.githubusercontent.com/${_pkgname}/${_pkgname}/v${pkgver}/install/linux/org.doublecmd.root.policy"
)
sha512sums=(
    '6bffd9b0256eae7ef12543e8350b2d5d3f0d36b155f0de5b36177e1f9c945f60b31ec82fbd7c7b98a0811409212743418f235927fae66e933f03a20f65ea4e8c'
    'a2e56171e34a752e0e9be4ba8aed83c8ad710248680fca5ae10c16b9f36d3ca25f6057deec35db31e2b59149de5d4f6bc3b94a3896d9913c06c205f3e29327c8'
    '2a82b0578c7428d4e2df6aadf09041f71b7bfed2773f62658b461309f18d6a444bc68fda24f58709d6ddcf166b95047ec6d261c4222b0cae0bfbcb14e7381f13'
    'b10ec792a3ccf978544b1b10e05ce9c6477008b3230ff89dc49084c7337e6df3f45cb36a0dc2675316609dcbf18d406d039f09cc0d5abb77f0d76179bad97200'
)

package() {
    cd "$srcdir/doublecmd"

    install -d "$pkgdir/usr/lib/doublecmd"
    cp -a . "$pkgdir/usr/lib/doublecmd/"
    rm -rf "$pkgdir/usr/lib/doublecmd/settings"

    install -d "$pkgdir/usr/bin"
    ln -s /usr/lib/doublecmd/doublecmd "$pkgdir/usr/bin/doublecmd"

    install -Dm644 "$srcdir/doublecmd.desktop" "$pkgdir/usr/share/applications/doublecmd.desktop"
    install -Dm644 doublecmd.png "$pkgdir/usr/share/pixmaps/doublecmd.png"
    install -Dm644 pixmaps/mainicon/alt/dcfinal.svg "$pkgdir/usr/share/icons/hicolor/scalable/apps/doublecmd.svg"

    install -Dm644 "$srcdir/doublecmd.1" "$pkgdir/usr/share/man/man1/doublecmd.1"
    gzip -n "$pkgdir/usr/share/man/man1/doublecmd.1"

    install -Dm644 "$srcdir/org.doublecmd.root.policy" "$pkgdir/usr/share/polkit-1/actions/org.doublecmd.root.policy"
}
