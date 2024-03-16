# Maintainer: Carlos Aznarán <caznaranl@uni.pe>
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor: Thomas Baechler <thomas@archlinux.org>

pkgname=davfs2
pkgver=1.7.0
pkgrel=1
pkgdesc="File system driver that allows you to mount a WebDAV folder"
arch=('armv7h' 'aarch64' 'x86_64')
url="https://savannah.nongnu.org/projects/${pkgname}"
license=('GPL')
depends=('neon' 'po4a')
backup=(etc/${pkgname}/${pkgname}.conf etc/${pkgname}/secrets)
source=(https://mirror.easyname.at/nongnu/${pkgname}/${pkgname}-${pkgver}.tar.gz{,.sig} davfs2-1.7.0-neon-0.33-support.patch)
validpgpkeys=('51A0F4A0C8CFC98F842EA9A8B94556F81C85D0D5') # Ali Abdallah <aabdallah@suse.com>
sha512sums=('6ee5820b60ed28ad100949bb4db65ea07bbae1ad0128cd35e7bb69f7f6bdde99606e8cf704ddb197f1400abadc3934d34ab85f298f9100b6ea9e60813c2345f2'
            'SKIP'
            'd4913a230f6cd5a5937ef10c77083935831d5725b944ff910a1d93d839d302a33def13fab4d7b59b2c8b9865b71b8d6a39414ca6a9f3dda9bebf727e65697b3b')

prepare() {
    cd $pkgname-$pkgver
    patch --forward --strip=1 --input=../davfs2-1.7.0-neon-0.33-support.patch
    ./bootstrap
}

build() {
  cd ${pkgname}-${pkgver}
  dav_user=nobody dav_group=network ./configure --prefix=/usr --sbindir=/usr/bin --sysconfdir=/etc --disable-debug
  make
}

package() {
  cd ${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install
}
