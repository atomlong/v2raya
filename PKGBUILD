# Maintainer: mzz2017 <m@mzz.pub>

pkgname=v2raya
pkgver=0.7.0.6
pkgrel=1
install=.INSTALL
pkgdesc="A web GUI client of Project V which supports V2Ray, SS, SSR, Trojan and Pingtunnel protocols"
arch=('i686' 'x86_64' 'armv7h' 'armv6h' 'aarch64')
url="https://github.com/mzz2017/v2rayA"
license=('GPL')
depends=('glibc' 'v2ray')
makedepends=('go>=2:1.12.3-1')
source=("$pkgname-$pkgver.tar.gz::https://github.com/mzz2017/v2rayA/archive/v$pkgver.tar.gz")
sha512sums=('SKIP')

build() {
    cd "v2rayA-$pkgver/service"
    export GO111MODULE=on
    export GOPROXY=https://goproxy.io
    go build -ldflags="-X v2rayA/global.Version=$pkgver" -o v2raya
}

package() {
    cd "$srcdir/v2rayA-$pkgver"
    
    install -Dm644 "install/universal/v2raya.service" "$pkgdir/usr/lib/systemd/system/v2raya.service"
    install -Dm755 "service/v2raya" -t "$pkgdir/usr/bin/"

    install -Dm644 "gui/public/img/icons/android-chrome-512x512.png" "$pkgdir/usr/share/icons/v2raya.png"
    install -Dm755 "install/universal/v2raya.desktop" -t "$pkgdir/usr/share/applications/"
}
