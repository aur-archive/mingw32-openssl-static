pkgname=mingw32-openssl-static
pkgver=1.0.1c
pkgrel=1
arch=(any)
url="http://www.openssl.org"
pkgdesc="The Open Source toolkit for Secure Sockets Layer and Transport Layer Security (mingw32, static)"
depends=(mingw32-runtime mingw32-zlib-static)
makedepends=('mingw32-w32api' 'mingw32-gcc' 'mingw32-binutils')
conflicts=('mingw32-openssl')
provides=('mingw32-openssl')
license=("BSD")
source=("http://www.openssl.org/source/openssl-$pkgver.tar.gz")
md5sums=('ae412727c8c15b67880aef7bd2999b2e')
options=(!strip !buildflags)

build()
{
  cd "$srcdir/openssl-$pkgver"
  unset LDFLAGS
  ./Configure \
    --cross-compile-prefix=i486-mingw32- \
    -DOPENSSL_NO_CAPIENG \
    --prefix=/usr/i486-mingw32 \
    mingw \
    no-shared \
    zlib
  make
}

package() {
  cd "$srcdir/openssl-$pkgver"
  mkdir -p "$pkgdir/usr/i486-mingw32/lib"
  cp libssl.a "$pkgdir/usr/i486-mingw32/lib/"
  cp libcrypto.a "$pkgdir/usr/i486-mingw32/lib/"
  cp -rf include "$pkgdir/usr/i486-mingw32/"
  i486-mingw32-strip -g $pkgdir/usr/i486-mingw32/lib/*.a
}

