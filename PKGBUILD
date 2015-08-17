# Maintainer: jason ryan <jasonwryan@gmail.com>
# Contributor: Thomas Dziedzic < gostrc at gmail >
# Contributor: Ondrej Martinak <omartinak@gmail.com>
# Contributor: Stefan Husmann <stefan-husmann@t-online.de>

pkgname=vifm-git
_gitname='vifm'
pkgver=4688.8c8b3f3
pkgrel=2
pkgdesc='Ncurses based file manager with vi like keybindings.'
arch=('i686' 'x86_64')
url='http://vifm.info/'
license=('GPL')
depends=('bash' 'ncurses')
makedepends=('git')
conflicts=('vifm')
provides=('vifm')
source=("vifm::git+https://github.com/$_gitname/$_gitname.git")
sha1sums=('SKIP')

pkgver() {
    cd "$srcdir"/"$_gitname"
    echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
    cd "$srcdir"/"$_gitname"
    ./autogen.sh
    ./configure --prefix=/usr 
    make 
}

package() {
  cd "$srcdir/$_gitname"
  make DESTDIR="$pkgdir/" install
  install -D -m644 COPYING "$pkgdir"/usr/share/licenses/"$_gitname"/COPYING 
}

