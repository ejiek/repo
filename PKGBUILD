# Maintainer: zimbatm <zimbatm@zimbatm.com>
# Maintainer: ShadowKyogre <shadowkyogre.public+aur@gmail.com>
# Maintainer: rmorgans <rick.morgans@gmail.com>
pkgname=direnv
pkgver=2.21.3
pkgrel=2
pkgdesc='a shell extension that manages your environment'
arch=('x86_64' 'i686' 'armv7h')
url='https://direnv.net'
license=('MIT')
makedepends=('go')
source=("$pkgname-$pkgver.tar.gz::https://github.com/direnv/direnv/archive/v$pkgver.tar.gz")
sha256sums=('012651a79e47150de4a386d1c3c81a017d5ceac14f5a0c24b0596a2215cde8be')

_gopackagepath=github.com/direnv/direnv

build() {
  cd "$pkgname-$pkgver"
  export CGO_CPPFLAGS="${CPPFLAGS}"
  export CGO_CFLAGS="${CFLAGS}"
  export CGO_CXXFLAGS="${CXXFLAGS}"
  export CGO_LDFLAGS="${LDFLAGS}"
  export GOFLAGS="-buildmode=pie -trimpath -mod=vendor -modcacherw"
  go build -o $pkgname
}

check() {
  cd "$pkgname-$pkgver"
  go test -v
  bash ./test/direnv-test.bash
  ./test/stdlib.bash
}

package() {
  cd "$pkgname-$pkgver"
  make install DESTDIR="$pkgdir/usr"
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
