# Maintainer: Danila Kiver <danila.kiver@mail.ru>
# Contributor: Tavian Barnes <tavianator@tavianator.com>
# Contributor: ah-OOG-ah

pkgname=java21-openjdk-hsdis-binutils
_major_ver=21
_minor_ver=0
_patch_ver=8
_update_ver=4
_git_tag=jdk-${_major_ver}.${_minor_ver}.${_patch_ver}+${_update_ver}
pkgver=${_major_ver}.${_minor_ver}.${_patch_ver}.u${_update_ver}
pkgrel=1
pkgdesc="Disassembler for HotSpot, binutils backend"
arch=('x86_64')
url='http://openjdk.java.net/'
license=('GPL2')
source=(https://github.com/openjdk/jdk${_major_ver}u/archive/${_git_tag}.tar.gz)
sha256sums=('b4197c33a0b9cd6aba09b8dfad5d408339ea6bf393e93680c5f1f28f939790c3')
depends=('llvm>=13.0.0')
conflicts=('java21-openjdk-hsdis' 'java21-openjdk-hsdis-llvm')
options=('!makeflags')

_jdk_src_root=jdk${_major_ver}u-jdk-${_major_ver}.${_minor_ver}.${_patch_ver}-${_update_ver}

build() {
    cd "${srcdir}/${_jdk_src_root}"

    bash configure \
        --with-hsdis=llvm \
        --disable-warnings-as-errors

    make build-hsdis
}

package() {
    cd "${srcdir}/${_jdk_src_root}"

    install -D -m755 \
        build/linux-x86_64-server-release/support/hsdis/hsdis-amd64.so \
        "${pkgdir}/usr/lib/jvm/java-21-openjdk/lib/hsdis-amd64.so"
}
