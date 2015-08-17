# Maintainer: archtux <antonio dot arias99999 at gmail dot com>

pkgname=pysoulseek
pkgver=1.2.7c
pkgrel=3
pkgdesc="Soulseek music-sharing client"
arch=('any')
url="http://sensi.org/~ak/pyslsk/"
license=('GPL2')
depends=('wxpython2.8')
optdepends=('pyvorbis: Others can see bitrates and lengths of Ogg Vorbis files that you share')
source=(http://sensi.org/~ak/pyslsk/pyslsk-$pkgver.tar.gz
        $pkgname.desktop)
md5sums=('65b1849eb7fe8c3552e3dea6843b53b7'
         '798b26c4fb31c79eb3ecc9ea875551b3')

prepare() {
  cd $srcdir/pyslsk-$pkgver

  # New Soulseek server address
  sed -i 's_2240_2242_' pysoulseek/config.py

  # wxPython fix
  sed -i 's_rel\ =\ wxPython.wx.wxRELEASE\_NUMBER_rel\ =\ 1_' pyslsk

  # Make Pysoulseek work with wxPython2.8
  sed -i '28i\	import wxversion\      	' pyslsk
  sed -i "29i\	wxversion.select('2.8')\      	" pyslsk   
}

package() {
  cd $srcdir/pyslsk-$pkgver

  # Install
  python2 setup.py install --root=$pkgdir/ --optimize=1

  # Desktop icon
  install -Dm644 ./img/bird.jpg $pkgdir/usr/share/pixmaps/pysoulseek.jpg
  install -Dm644 $startdir/$pkgname.desktop $pkgdir/usr/share/applications/$pkgname.desktop

  # Remove Windows stuff
  rm $pkgdir/usr/bin/pyslsk-import-winconfig
}