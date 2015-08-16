# Contributor: danitool

pkgname=netdiscover-patched
pkgver=0.3
pkgrel=3
pkgdesc="Netdiscover is an active/passive address reconnaissance tool, mainly developed for those wireless networks without dhcp server, when you are wardriving. It can be also used on hub/switched networks."
arch=('i686' 'x86_64')
url="http://nixgeneration.com/~jaime/netdiscover/"
license=('GPL')
depends=('libnet' 'libpcap')
provides=('netdiscover')
conflicts=('netdiscover')
source=("http://nixgeneration.com/~jaime/netdiscover/releases/netdiscover-$pkgver-beta6.tar.gz"
        'misc.diff' 'oui.diff')
md5sums=('0919227a91ecaeeb2443cff249417be2'
         '14e7a2497e4889f540f8033482437660'
         '24f8e054b579810273896f410ca2b420')

prepare() {
    cd "$srcdir/netdiscover-$pkgver-beta6"
    patch -p0 -i $srcdir/oui.diff
    patch -p0 -i $srcdir/misc.diff
}

build() {
    cd "$srcdir/netdiscover-$pkgver-beta6"
    ./configure \
        --prefix=/usr \
        --mandir=/usr/share/man
    make
}

package() {
    cd "$srcdir/netdiscover-$pkgver-beta6"
    make DESTDIR="$pkgdir" install
    install -dm755 "$pkgdir/usr/share/"
    mv "$pkgdir/usr/doc" "$pkgdir/usr/share/"
}
