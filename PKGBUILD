# Maintainer: Mathieu Clabaut <mathieu.clabaut@gmail.com>

pkgname=diff-pdf
pkgver=20120607
pkgrel=2
pkgdesc="Tool for visually comparing two PDF files"
url="https://github.com/vslavik/diff-pdf"
license=('GPL')
arch=(i686 x86_64)

depends=('poppler-qt' 'wxgtk' 'poppler-glib')
makedepends=('git')
source=()
md5sums=()

_gitroot=https://github.com/vslavik/diff-pdf.git
_gitname=diff-pdf

build () {
   cd "$srcdir"
   if [ -d $_gitname ]; then
	 (cd $_gitname && git reset HEAD --hard && git clean -x -d -f && git pull origin)
	 msg "Updated the local files."
   else
	 git clone $_gitroot
	 msg "GIT checkout done or server timeout"
   fi

   cd $_gitname
   ./bootstrap
   ./configure --prefix=/usr
   make || return 1
}

package() {
    cd "$srcdir"/$_gitname
    make DESTDIR="$pkgdir" install || return 1
}
