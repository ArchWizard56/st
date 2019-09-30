# Maintainer: Archwizard <archwizard101@gmail.com>
pkgname=st-solarized
pkgver=0.8.1
pkgrel=0
pkgdesc="the Suckless Terminal with Archwizard's patches applied"
arch=('x86_64')
url="https://st.suckless.org"
license=('MIT')
depends=('libxft' 'ttf-droid')
makedepends=('git' 'ncurses' 'libxext')
conflicts=('st' 'st-solarized-git')
changelog=
source=("$pkgname-$pkgver::https://dl.suckless.org/st/st-$pkgver.tar.gz"
        "https://st.suckless.org/patches/solarized/st-solarized-dark-20180411-041912a.diff"
	"https://st.suckless.org/patches/clipboard/st-clipboard-20180309-c5ba9c0.diff"
	"https://st.suckless.org/patches/scrollback/st-scrollback-mouse-altscreen-0.8.diff"
	"https://st.suckless.org/patches/scrollback/st-scrollback-0.8.diff"
	"https://st.suckless.org/patches/scrollback/st-scrollback-mouse-0.8.diff"
	"st-archwizardDroidFont-20181226.diff")

md5sums=('92135aecdba29300bb2e274a55f5b71e'
         '3a1a347e1489d7bde6b68faff6cc19a0'
         '87f715392760fe62ebba09db4b89113d'
         '53a430a1b2da077b170279d09abf1b72'
         'bbe056eaed5914f55ccea001ca7f05e9'
         '72227737f6cd831afd014a3613bd559d'
         '7e87286705a5ac141517c83980510353')
prepare() {
	cd "st-$pkgver"
	patch -p1 -i "$srcdir/st-scrollback-0.8.diff"
	patch -p1 -i "$srcdir/st-scrollback-mouse-0.8.diff"
	patch -p1 -i "$srcdir/st-scrollback-mouse-altscreen-0.8.diff"
	patch -p1 -i "$srcdir/st-solarized-dark-20180411-041912a.diff"
	patch -p1 -i "$srcdir/st-clipboard-20180309-c5ba9c0.diff"
	patch -p1 -i "$srcdir/st-archwizardDroidFont-20181226.diff"
	sed -i '/mkdir -p $(DESTDIR)$(MANPREFIX)\/man1/,+4d' "Makefile"

}

build() {
	cd "st-$pkgver"
	make
}

package() {
	cd "st-$pkgver"
	make DESTDIR="$pkgdir/" install
}
