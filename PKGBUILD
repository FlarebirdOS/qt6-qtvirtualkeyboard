pkgname=qt6-qtvirtualkeyboard
pkgver=6.9.2
pkgrel=1
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
sha256sums=(0a906801540e542309f62c02a75befa1e2742393db2948abf72959421c1aa6c7)

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
