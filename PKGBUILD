# Maintainer: manjaro <manjaro-dev@garetech.com.au>
pkgname="snoopy"
pkgver=2.4.6
pkgrel="$( uname -r | cut -d\. -f1-2 )"
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
md5sums=("SKIP")
validpgpkeys=()

pkgver() {
  # ver="2.4.6-36-g4eb2bb9"
  pkgver="$( cd "${srcdir}/${pkgname}" && ./build/get-version.sh  | cut -d\- -f1)"
  echo "${pkgver}"
}

prepare() {
	pwd
}

build() {
        pwd
        cd "${srcdir}/${pkgname}"
        pwd
        bash bootstrap.sh 
	./configure --prefix=/ --exec-prefix=/usr --sbindir=/usr/bin
	make
}

check() {
	#cd  "${pkgname}-${pkgver}-${pkgrel}"
        cd "${srcdir}/${pkgname}"
	make -k check
}

package() {
	#cd "${pkgname}-${pkgver}-${pkgrel}"
        cd "${srcdir}/${pkgname}"
	make DESTDIR="$pkgdir/" install
        echo "/lib/libsnoopy.so" >> ${pkgdir}/etc/ld.so.preload
        chmod 644 ${pkgdir}/etc/ld.so.preload
}
