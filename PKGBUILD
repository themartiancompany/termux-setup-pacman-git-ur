## SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

if [[ -v "docs" ]]; then
  _docs="true"
fi
if [[ "${_git}" == "true" ]]; then
  _git="false"
fi
_py="python"
_pkg=termux-setup-pacman
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-docs"
  )
fi
pkgdesc="Script to setup a pacman environment on Termux."
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${_pkg}"
pkgver=0.1.1
pkgrel=2
license=(
  'AGPL3'
)
makedepends=(
  'make'
)
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
   'git'
  )
fi
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    "${_py}-docutils"
  )
fi
checkdepends=(
  'shellcheck'
)
optdepends=(
)
arch=(
  'any'
)
_git_uri="git+${url}.git#tag=${pkgver}"
_http_uri="${url}/archive/refs/tags/${pkgver}.tar.gz"
_tarname="${_pkg}-${pkgver}"
if [[ "${_git}" == "true" ]]; then
  _uri="${_git_uri}"
  _src="${_tarname}::${_git}#tag=${pkgver}"
elif [[ "${_git}" == "false" ]]; then
  _uri="${_http_uri}"
  _src="${_tarname}.tar.gz::${_uri}"
fi
source=(
  "${_src}"
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

package_termux-setup-pacman() {
  local \
    _make_opts=()
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${pkgname}-${pkgver}"
  make \
    "${_make_opts[@]}" \
      install-scripts
}

package_termux-setup-pacman-docs() {
  local \
    _make_opts=()
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${pkgname}-${pkgver}"
  make \
    "${_make_opts[@]}" \
      install-doc
  make \
    "${_make_opts[@]}" \
      install-man
}

# vim:set sw=2 sts=-1 et:
