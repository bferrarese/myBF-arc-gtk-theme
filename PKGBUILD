# My modified arc-gtk-theme with gdm support
#
# Original work from NicoHood <archlinux {cat} nicohood {dog} de>
# PGP ID: 97312D5EB9D7AE7D0BD4307351DAE9B7C1AE9161
# Contributor: zach <zach {at} zach-adams {dot} com>
# Contributor: Gordian Edenhofer <gordian.edenhofer[at]yahoo[dot]de
# Contributor: Philipp Wolfer <ph.wolfer@gmail.com>

_pkgname=arc-theme
pkgname=('myBF-arc-gtk-theme')
pkgdesc="A flat theme with transparent elements for GTK 3, GTK 2 and Gnome-Shell"
replaces=('arc-gtk-theme' 'gtk-theme-arc')
provides=('arc-gtk-theme')
conflicts=('arc-gtk-theme')
pkgver=$(date +%Y%m%d)
pkgrel=11
groups=('mypkgs')
arch=('any')
url="https://github.com/arc-design/arc-theme"
license=('GPL3')
optdepends=('arc-icon-theme: recommended icon theme'
            'gtk-engine-murrine: for gtk2 themes'
            'gnome-themes-standard: for gtk2 themes'
            # 'resvg: building the package faster'
            )
makedepends=('gtk3' 'sassc' 'optipng' 'inkscape' 'parallel')
source=("git+${url}")
sha512sums=('SKIP')

prepare() {
    find ./${_pkgname}/common/ -type f -exec sed -i'' -e 's/#5294e2/#ff3333/gI'  {} \; ;
    # sed -i 's/#5294e2/#ff3333/gI' ${_pkgname}/common/gnome-shell/3.32/sass/_colors.scss
    # sed -i 's/center top/0px 0px/' ${_pkgname}/common/gnome-shell/3.32/sass/_common.scss
}

build() {
    cd ${_pkgname}
    ./autogen.sh --prefix=/usr --with-gnome-shell=3.32 --disable-light --disable-darker --disable-cinnamon --disable-metacity --disable-unity --disable-xfwm --disable-plank --disable-openbox
}

package() {
    cd ${_pkgname}
    make DESTDIR="${pkgdir}" install
    install -Dm640 ${startdir}/newbackground.png ${pkgdir}/usr/share/gnome-shell/newbackground.png
    install -Dm640 ${startdir}/noise-texture.png ${pkgdir}/usr/share/gnome-shell/noise-texture.png
    install -Dm750 ${startdir}/update-gdm-background ${pkgdir}/usr/share/gnome-shell/update-gdm-background
    install -Dm640 ${startdir}/update-gdm-background.hook ${pkgdir}/etc/pacman.d/hooks/myBF-update-gdm-background.hook
}
