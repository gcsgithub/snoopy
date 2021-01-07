# Maintainer: manjaro <manjaro-dev@garetech.com.au>
pkgname=snoopy
pkgver=2.4.6
pkgrel=35
epoch=
pkgdesc="Snoopy-mg (Manjaro)"
arch=(aarch64 x86_64)
url="https://github.com/gcsgithub/snoopy.git"
license=("GPL")
groups=()
depends=()
makedepends=("git")
checkdepends=()
optdepends=()
provides=("snoopy-${pkgver}")
conflicts=("snoopy")
replaces=()
backup=("etc/snoopy.ini")
options=()
install=
changelog=
source=(git+${url}#branch=master)
noextract=()
md5sums=("356e72b6dfcacfd6ad5a4d5b66df7c6d"
         "72a90f76eafde1e09775a6f21927885d")


validpgpkeys=()

prepare() {
        git clone "${url}" "${pkgname}-${pkgver}-${pkgrel}"
}

build() {
	cd "${pkgname}-${pkgver}-${pkgrel}"
	./configure --prefix=/ --exec-prefix=/usr --sbindir=/usr/bin
	make
}

check() {
	cd  "${pkgname}-${pkgver}-${pkgrel}"
	make -k check
}

package() {
	cd "${pkgname}-${pkgver}-${pkgrel}"
	make DESTDIR="$pkgdir/" install
        echo "/lib/libsnoopy.so" >> ${pkgdir}/etc/ld.so.preload
        chmod 644 ${pkgdir}/etc/ld.so.preload
}
