# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/libmbim
# 						Maintainer: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgname=libmbim
pkgver=1.16.0
pkgrel=2
pkgdesc="MBIM modem protocol helper library"
arch=(x86_64)
url="https://www.freedesktop.org/wiki/Software/libmbim/"
license=(GPL2)
depends=('glib2' 'bash' 'libgudev')
makedepends=('gtk-doc' 'python' 'git' 'help2man')
_commit=16e15d49297f72397f6b691cf7a9ccf47bdae844 # tags/1.16.0
source=("git+https://anongit.freedesktop.org/git/libmbim/libmbim#commit=$_commit")
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

pkgver(){
	cd $pkgname
	git describe --tags | sed 's:-:+:g'
}

prepare(){
	cd $pkgname
	NOCONFIGURE=1 ./autogen.sh
}

build() {
  cd ${pkgname}
  ./configure 	--prefix=/usr \
				--sysconfdir=/etc \
				--localstatedir=/var \
				--libexecdir=/usr/lib/libmbim \
				--disable-static \
				--with-udev-base-dir=/usr/lib/udev \
				--enable-gtk-doc
  make
}

check() {
  cd ${pkgname}
  make check
}

package() {
  cd ${pkgname}
  make DESTDIR="$pkgdir" install
}
