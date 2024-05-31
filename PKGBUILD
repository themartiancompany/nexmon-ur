# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>
# Maintainer: Truocolo <truocolo@aol.com>

_pkg="nexmon"
pkgbase="${_pkg}"
pkgname=(
  # "${_pkg}"
  "fakeioctl"
)
pkgver="2.2.2"
pkgrel=1
_pkgdesc=(
   'C-based Firmware Patching Framework'
   'for Broadcom/Cypress WiFi Chips'
   'that enables Monitor Mode,'
   'Frame Injection and much more'
)
pkgdesc="${_pkgdesc[*]}"
url="https://${_pkg}.org"
license=(
  'GPLv3'
)
arch=(
  'x86_64'
  'arm'
  'aarch64'
)
depends=(
)
makedepends=(
  # 'git'
  make
)
provides=(
)
groups=(
  hip
)
_http="https://github.com"
_ns="seemoo-lab"
_url="${_http}/${_ns}/${_pkg}"
source=(
  # "${_pkg}-${pkgver}::git+${url}#tag=${pkgver}"
  "${_pkg}-${pkgver}.tar.gz::${_url}/archive/refs/tags/${pkgver}.tar.gz"
  # "${url}/-/archive/${pkgver}/${_pkg}-${pkgver}.tar.gz"
)
sha512sums=(
  'e393459e31ad2d05e71a2e573bc2ed8b8125f73cf8c717853fad71e1303d529c751b5876cc47a13e4416ded29762360400aeac596df3416138d382941f68d5ba'
)

_build_util() {
  local \
    _pkg="${1}" \
    _oldpwd
  _oldpwd="$( \
    pwd)"
  cd \
    "${srcdir}/${_pkg}-${pkgver}/utilities/${_pkg}"
  make
  ls
  cd \
    "${_oldpwd}"
}

# shellcheck disable=SC2154
_build_fakeioctl() {
  _build_util \
    "libfakeioctl"
}

build() {
  _build_fakeioctl
}

# shellcheck disable=SC2154
package_fakeioctl() {
  provides=(
    "libfakeioctl"
    "libfakeioctl.so"
  )
  cd \
    "${_pkg}-${pkgver}"
  install \
    -Dm644 \
    "utilities/libfakeioctl/libfakeioctl.so" \
    "${pkgdir}/usr/lib"
}

# vim:set sw=2 sts=-1 et:
