# Contributor: Patrick Schwalm

pkgname=osso-git
pkgver=20130313
pkgrel=1
pkgdesc="qt oss sound mixer"
url="http://github.com/antico/osso/tree/master"
arch=('i686' 'x86_64')
license=('GPL')
depends=('qt4' 'oss')
makedepends=('git')
conflicts=()
replaces=()
backup=()

_gitroot="git://github.com/antico/osso.git"
_gitname="osso"

build() {

  cd ${srcdir}
  msg "Connecting to git...."

  if [ -d ${srcdir}/$_gitname ] ; then
  cd $_gitname && git pull origin
  msg "The local files are updated."
  else
  git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cd $srcdir/osso/

  qmake-qt4 || return 1
  make

  mkdir -p $pkgdir/usr/
  mkdir -p $pkgdir/usr/bin/
  cp -a $srcdir/osso/osso $pkgdir/usr/bin/
  #make DESTDIR=${pkgdir} install || return 1

}
