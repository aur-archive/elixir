# Maintainer: Gilbert Kennen <gilbert firewatcher org>
pkgname=elixir
pkgver=1.0.3
pkgrel=2
pkgdesc="a functional meta-programming aware language built on top of the Erlang VM"
url="http://elixir-lang.org"
arch=('any')
license=('Apache' 'custom:EPL')
depends=('erlang-nox')
conflicts=()
replaces=()
backup=()
source=("https://github.com/elixir-lang/elixir/tarball/v${pkgver}")
sha512sums=('301a52450044fc571b87f1ae6e0c7a9a7069dc8a84bee9e497b06b6744e57f0bcea2b03622f1a55d5cd08fb944ae6b64d05e8c6797a167833d81e8ea4ab7ef7e')

prepare() {
  local elixir_src_dir=${srcdir}/$(tar "-tzf${srcdir}/v${pkgver}" | grep -o '^[^/]\+' | sort -u)
  rm -rf "${srcdir}/${pkgver}_src"
  mv $elixir_src_dir "${srcdir}/${pkgver}_src"
}

build() {
  cd "${srcdir}/${pkgver}_src"
  make
}

check() {
  cd "${srcdir}/${pkgver}_src"
  make test_erlang
}

package() {
  mkdir -p "${pkgdir}/usr/share/licenses/${pkgname}"

  cd "${srcdir}/${pkgver}_src"

  install -Dm644 {LEGAL,LICENSE} "${pkgdir}/usr/share/licenses/${pkgname}"

  make DESTDIR=$pkgdir PREFIX=/usr install
}