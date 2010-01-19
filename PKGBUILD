#!/usr/bin/makepkg -p
# Maintainer:  Matthew Bauer <mjbauer95@gmail.com>
pkgname=uniconv-git
pkgver=20100118
pkgrel=1
pkgdesc="UniConv will convert input to output with support for many formats (using imagemagick, ffmpeg, mplayer, ps2pdf)"
arch=(i686 x86_64)
url=""
license=('GPL')
depends=()
optdepends=()
makedepends=()
provides=(uniconv)

_gitroot="git://github.com/paradoq/uniconv.git"
_gitname="$pkgname-$pkgver"

build() {
	cd "${srcdir}"

	msg "Connecting to github.com GIT server...."

	if [ -d "${srcdir}/$_gitname" ] ; then
		cd "$_gitname" && git pull origin || return 1
		msg "The local files are updated."
	else
		git clone "$_gitroot" "$_gitname"
		cd "$_gitname"
	fi

	msg "GIT checkout done"
	msg "Starting install..."

	mkdir -p $pkgdir/usr/bin
	cp $srcdir/bin/* $pkgdir/usr/bin

	mkdir -p $pkgdir/usr/share/uniconv
	cp $srcdir/conversions $pkgdir/usr/share/uniconv

	mkdir -p $pkgdir/usr/share/man/man1
	gzip $srcdir/MAN -c > $pkgdir/usr/share/man/man1/uniconv.1.gz
}
