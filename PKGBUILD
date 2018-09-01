pkgname=adapta-gtk-theme
pkgver=3.94.0.143
pkgrel=1
pkgdesc='An adaptive Gtk+ theme based on Material Design Guidelines'
arch=('x86_64')
url='https://github.com/adapta-project/adapta-gtk-theme'
license=('CCPL' 'GPL2')
depends=('gtk3')
makedepends=('gdk-pixbuf2' 'inkscape' 'parallel' 'libxml2' 'sassc')
optdepends=('gtk2'
            'gtk-engine-murrine: for gtk2 themes')
source=("${url}/archive/${pkgver}.tar.gz")
md5sums=('4851c353ea0b2f4652e32ab26d2f5e93')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  ./autogen.sh \
    --prefix='/usr' \
    --enable-parallel \
    --enable-plank \
    --enable-telegram \
    --disable-unity
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  make DESTDIR="${pkgdir}" install

  install -dm 755 "${pkgdir}"/usr/share/plank/themes
  ln -s /usr/share/themes/Adapta/plank "${pkgdir}"/usr/share/plank/themes/Adapta

  install -Dm 644 LICENSE_CC_BY_SA4 -t "${pkgdir}"/usr/share/licenses/adapta-gtk-theme/
}
