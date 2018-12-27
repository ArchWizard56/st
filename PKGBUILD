# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Archwizard <archwizard101@gmail.com>
pkgname=st-solarized-git
pkgver=1
pkgrel=1
epoch=
pkgdesc="the Suckless Terminal with archwizard's patches applied"
arch=('x86_64')
url="https://st.suckless.org"
license=('GPL')
depends=('libxft' 'ttf-droid')
makedepends=('git' 'ncurses' 'libxext')
conflicts=('st')
changelog=
source=("$pkgname-$pkgver::git://git.suckless.org/st"
        "https://st.suckless.org/patches/solarized/st-solarized-dark-20180411-041912a.diff"
	"https://st.suckless.org/patches/clipboard/st-clipboard-20180309-c5ba9c0.diff"
	"st-archwizardDroidFont-20181226.diff")
md5sums=('SKIP'
         '3a1a347e1489d7bde6b68faff6cc19a0'
         '87f715392760fe62ebba09db4b89113d'
         '7e87286705a5ac141517c83980510353')
prepare() {
	cd "$pkgname-$pkgver"
	patch -p1 -i "$srcdir/st-solarized-dark-20180411-041912a.diff"
	patch -p1 -i "$srcdir/st-clipboard-20180309-c5ba9c0.diff"
	patch -p1 -i "$srcdir/st-archwizardDroidFont-20181226.diff"
}

build() {
	cd "$pkgname-$pkgver"
	make
}

package() {
	cd "$pkgname-$pkgver"
	make DESTDIR="$pkgdir/" install
}
