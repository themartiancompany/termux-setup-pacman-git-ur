# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>

pkgbase=termux-setup-pacman
pkgname=(
  "${pkgbase}"
)
pkgdesc="Script to setup a pacman environment on Termux."
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgbase}"
pkgver=0.1.1
pkgrel=2
license=(
  'AGPL3'
)
makedepends=(
  # 'git'
)
checkdepends=(
  'shellcheck'
)
optdepends=(
)
arch=(
  any
)
_git="git+${url}.git#tag=${pkgver}"
_http="${url}/archive/refs/tags/${pkgver}.tar.gz"
source=(
  # "${pkgname}::${_git}#tag=${pkgver}"
  "${pkgname}-${pkgver}.tar.gz::${_http}"
)
sha256sums=(
  '17700db7892ea7055e998fe8e686e0e40a0f47e3f9fb7c1a608943876bcba165'
)

check() {
  cd \
    "${pkgname}"
  make \
    -k \
    check
}

package() {
  local \
    _opts=()
  _opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${pkgname}-${pkgver}"
  make \
    "${_opts[@]}" \
      install
}

# vim:set sw=2 sts=-1 et:
