# Maintainer: Jerome Leclanche <jerome@leclan.ch>

_pkgname=Heartbleed
pkgname=heartbleed-git
pkgver=v0.2.0.1.geecd019
pkgrel=1
pkgdesc="Test whether a host is vulnerable to the Heartbleed attack"
arch=('any')
_url="github.com/FiloSottile/Heartbleed"
url="https://$_url"
license=("MIT")
makedepends=('git' 'go')
source=("$_url::git://github.com/FiloSottile/Heartbleed.git")
sha256sums=('SKIP')

pkgver() {
	cd "$srcdir/$_pkgname"
	git describe --always | sed "s/-/./g"
}

build() {
	cd "$srcdir"
	# makepkg doesn't support extracting sources to a specific directory
	mkdir -p src/$_url && rm -rf src/$_url && mv $_pkgname src/$_url && cd src/$_url
	GOPATH="$srcdir" go get -d -t github.com/FiloSottile/Heartbleed
}

package() {
	cd "$srcdir"
	GOPATH="$srcdir" go build -v github.com/FiloSottile/Heartbleed

	mkdir -p "$pkgdir/usr/bin"
	cp "$srcdir/Heartbleed" "$pkgdir/usr/bin/heartbleed"
}
