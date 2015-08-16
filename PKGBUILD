# Maintainer: Linus Sjögren <thelinx@unreliablepollution.net>
# Contributor: Eric Forgeot < http://anamnese.online.fr >, dreeze
pkgname=love-jit
pkgver=0.7.2
pkgrel=1
pkgdesc="An open-source 2D game engine which uses the versatile Lua scripting language to create dynamic gaming experiences. This package uses LuaJIT as a backend."
arch=(i686 x86_64)
url="http://love2d.org/"
license=('zlib')
depends=('luajit2' 'physfs' 'freetype2' 'devil' 'mpg123' 'openal' 'libvorbis' 'libmodplug' 'shared-mime-info' 'hicolor-icon-theme' 'desktop-file-utils')
makedepends=('wget')
install=love.install
conflicts=('love')
provides=('love')
source=("https://bitbucket.org/rude/love/downloads/love-$pkgver-linux-src.tar.gz"
        "https://bitbucket.org/rude/love/raw/$pkgver/license.txt"
        "https://bitbucket.org/rude/love/raw/$pkgver/platform/unix/app.svg"
        "https://bitbucket.org/rude/love/raw/$pkgver/platform/unix/game.svg"
        "https://bitbucket.org/rude/love/raw/$pkgver/platform/unix/love.desktop"
        "https://bitbucket.org/rude/love/raw/$pkgver/platform/unix/love.xml")
md5sums=('c3e678606bb9a870c31168e85b269e7e'
         'a4890908149d91bc042b30d00c121c58'
         'a1e19f91420cc519a683af360f5b1120'
         '16f2ecc899c9ffc8b7b7c807f8967861'
         '971bec1bffe4f424972eef2a26d27bec'
         'b4f00fb1cb80057a0a371a994100d418')

build() {
  cd "$srcdir/love-HEAD"
  ./configure --prefix=/usr --enable-luajit LDFLAGS="$LDFLAGS -Wl,--no-as-needed"
  make
}

package() {
  cd "$srcdir/love-HEAD"
  make DESTDIR="$pkgdir" install

  mkdir -p "$pkgdir/usr/share/licenses/$pkgname"
  mkdir -p "$pkgdir/usr/share/icons/hicolor/scalable/mimetypes"
  mkdir -p "$pkgdir/usr/share/icons/hicolor/scalable/apps"
  mkdir -p "$pkgdir/usr/share/applications"
  mkdir -p "$pkgdir/usr/share/mime/packages"

  install -Dm0644 "$srcdir/license.txt" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm0644 "$srcdir/app.svg" \
    "$pkgdir/usr/share/icons/hicolor/scalable/apps/love.svg"
	install -Dm0644 "$srcdir/game.svg" \
    "$pkgdir/usr/share/icons/hicolor/scalable/mimetypes/gnome-mime-application-x-love-game.svg"
  install -Dm0644 "$srcdir/love.desktop" \
    "$pkgdir/usr/share/applications/$pkgname.desktop"
  install -Dm0644 "$srcdir/love.xml" \
    "$pkgdir/usr/share/mime/packages/love.xml"
}

# vim:set ts=2 sw=2 et:
