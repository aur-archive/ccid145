# Contributor: acounto <acounto@kamikakushi.net>

pkgname=ccid145
_pkgname=ccid
pkgver=1.4.5
_pkgver=1.4.4
pkgrel=1
pkgdesc="Earlier version of ccid (1.4.5). This supports SCR3310-NTTCom."
arch=('i686' 'x86_64')
url="http://pcsclite.alioth.debian.org/ccid.html"
license=('LGPL' 'GPL')
depends=('pcsclite')
conflicts=('ccid')
provides=('ccid=1.4.5')
backup=(etc/reader.conf.d/libccidtwin)
source=("https://alioth.debian.org/frs/download.php/3579/$_pkgname-$pkgver.tar.bz2")
md5sums=('79ef91103bcdd99a3b31cb5c5721a829')

build() {
  cd $srcdir/$_pkgname-$_pkgver
  ./configure \
    --enable-twinserial \
    --prefix=/usr \
    --sysconfdir=/etc
  make
}

package() {
  cd $srcdir/$_pkgname-$_pkgver
  make DESTDIR=$pkgdir install
  install -D -m644 src/92_pcscd_ccid.rules  $pkgdir/lib/udev/rules.d/85-pcscd-ccid.rules
}
