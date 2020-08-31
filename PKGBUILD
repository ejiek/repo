# Maintainer: morpheusthewhite <zffromGerace@hotmail.it>

pkgname=spicetify-themes-git
pkgver=r424.17d0670
pkgrel=1
pkgdesc="A community-driven collection of themes for spicetify"
arch=('any')
url="https://github.com/morpheusthewhite/spicetify-themes"
license=('MIT')
groups=()
depends=('spicetify-cli')
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
backup=()
options=()
install=spicetify-themes-git.install
source=("$pkgname"::"git+https://github.com/morpheusthewhite/spicetify-themes")
noextract=()
md5sums=('SKIP')

pkgver() {
    cd "$pkgname"
    ( set -o pipefail
      git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
      printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
    )
}

package() {
    mkdir -p "${pkgdir}"/usr/share/spicetify-cli/Extensions

    cp -R "$srcdir/${pkgname}" "${pkgdir}"/usr/share/spicetify-cli/Themes
    rm -r "${pkgdir}"/usr/share/spicetify-cli/Themes/README.md "${pkgdir}"/usr/share/spicetify-cli/Themes/LICENSE

    # for Dribbblish theme
    cp -R "$srcdir/${pkgname}/Dribbblish/dribbblish.js" "${pkgdir}"/usr/share/spicetify-cli/Extensions/dribbblish.js
}
