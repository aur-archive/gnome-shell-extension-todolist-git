# Contributor: Florian Bäuerle <florian.bae@gmail.com>

pkgname=gnome-shell-extension-todolist-git
pkgver=20120205
pkgrel=2
pkgdesc="Simple todo list extension for gnome-shell"
arch=('any')
url="https://github.com/bsaleil/todolist-gnome-shell-extension"
groups=('gnome-shell-extensions')
license=('unknown')
depends=('gnome-shell')

_gitroot="https://github.com/bsaleil/todolist-gnome-shell-extension.git"
_gitname="todolist-gnome-shell-extension"

build() {
  msg "Connecting to GIT server...."

  if [ -d $startdir/src/$_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"
}

package() {
    cd $srcdir/$_gitname
    patch metadata.json <<EOF
2c2
< 	"shell-version": ["3.2.1"], 
---
> 	"shell-version": ["3.2"], 
EOF
    install -Dm644 extension.js $pkgdir/usr/share/gnome-shell/extensions/todolist@bsaleil.org/extension.js
    install -Dm644 metadata.json $pkgdir/usr/share/gnome-shell/extensions/todolist@bsaleil.org/metadata.json    
    install -Dm644 list.tasks $pkgdir/usr/share/gnome-shell/extensions/todolist@bsaleil.org/list.tasks
    install -Dm644 stylesheet.css $pkgdir/usr/share/gnome-shell/extensions/todolist@bsaleil.org/stylesheet.css
}

