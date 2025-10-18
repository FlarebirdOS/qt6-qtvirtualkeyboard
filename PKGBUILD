pkgname=qt6-qtvirtualkeyboard
pkgver=6.10.0
pkgrel=2
pkgdesc="Virtual keyboard framework"
arch=('x86_64')
url="https://www.qt.io"
license=(
    'GPL-3.0-only'
    'LGPL-3.0-only'
    'LicenseRef-Qt-Commercial'
    'Qt-GPL-exception-1.0'
)
depends=(
    'gcc-libs'
    'glibc'
    'hunspell'
    'qt6-qtbase'
    'qt6-qtdeclarative'
    'qt6-qtmultimedia'
    'qt6-qtsvg'
)
makedepends=(
    'cmake'
    'git'
    'ninja'
)
source=(git+https://code.qt.io/qt/${pkgname#*-}#tag=v${pkgver})
sha256sums=(cdcfa0cc12111fa6d8afba38db3ac45f39e27c41d3feabca28e63667f8d467d7)

build() {
    cd ${pkgname#*-}

    local cmake_args=(
        -B flarebird-build
        -G Ninja
        -D CMAKE_BUILD_TYPE=Release
        -D CMAKE_INSTALL_PREFIX=/usr
        -D INSTALL_LIBDIR=lib64
        -D CMAKE_MESSAGE_LOG_LEVEL=STATUS
    )

    cmake "${cmake_args[@]}"

    cmake --build flarebird-build
}

package() {
    cd ${pkgname#*-}

    DESTDIR=${pkgdir} cmake --install flarebird-build
}
