# Maintainer: manjaro <manjaro-dev@garetech.com.au>
pkgname="snoopy"
pkgver=2.4.6
pkgrel=55
epoch=
pkgdesc="Snoopy-mg (Manjaro)"
arch=(aarch64 x86_64)
url="https://github.com/gcsgithub/snoopy.git"
license=("GPL")
groups=()
depends=("git")
makedepends=()
checkdepends=()
optdepends=()
provides=("${pkgname}-${pkgver}")
conflicts=("${pkgname}")
replaces=()
backup=("etc/snoopy.ini")
options=()
install=
changelog=
branch="master"
source=(git+${url}#branch=${branch})
noextract=()
md5sums=("SKIP")
validpgpkeys=()

pkgver() {
        pkgver="$( cd "${srcdir}/${pkgname}" && ./build/get-version.sh  | cut -d\- -f1)"
        echo "${pkgver}"
}

#prepare() {
#}

build() {
        cd "${srcdir}/${pkgname}"
        pwd
        bash bootstrap.sh 
        ./configure --prefix=/ --exec-prefix=/usr --sbindir=/usr/bin
        make
}

check() {
        cd "${srcdir}/${pkgname}"
        make -k check
}

package() {
        cd "${srcdir}/${pkgname}"
        make DESTDIR="$pkgdir/" install
        echo "/lib/libsnoopy.so" >> ${pkgdir}/etc/ld.so.preload
        chmod 644 ${pkgdir}/etc/ld.so.preload
}
