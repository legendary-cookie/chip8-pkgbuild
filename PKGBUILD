# Maintainer: Vincent Schweiger <github.com@xolley.de>
pkgname=chip8-git
pkgver=r87.4dfed2b
pkgrel=1
pkgdesc="Chip8 assembler, disassembler and emulator"
arch=('any')
url="https://github.com/wernsey/chip8"
license=('GPL')
groups=()
depends=()
makedepends=('git', 'wget') # 'bzr', 'git', 'mercurial' or 'subversion'
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
replaces=()
backup=()
options=()
install=
source=('chip8::git+https://github.com/wernsey/chip8')
noextract=()
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
# Git, no tags available
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd "$srcdir/${pkgname%-git}"
	wget https://raw.githubusercontent.com/legendary-cookie/chip8-pkgbuild/master/git.patch -O $srcdir/git.patch
	git apply $srcdir/git.patch
}

build() {
	cd "$srcdir/${pkgname%-git}"
	make
}

check() {
	cd "$srcdir/${pkgname%-git}"
}

package() {
	cd "$srcdir/${pkgname%-git}"
	make DESTDIR="$pkgdir/usr" install
}
