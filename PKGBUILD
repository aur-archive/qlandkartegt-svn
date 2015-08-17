# Contributor: Matthias Maennich <arch@maennich.net>
# Maintainer: Alexander 'hatred' Drozdov <adrozdoff@gmail.com>
pkgname=qlandkartegt-svn
pkgver=3655
pkgrel=1
pkgdesc="Use your Garmin GPS with Linux (SVN Version)"
arch=('i686' 'x86_64')
url="http://www.qlandkarte.org"
license=('GPL')
depends=('proj>=4.4' 'libusb>=0.1' 'gdal' 'qt4>=4.3' 'xerces-c')
makedepends=('subversion' 'cmake')
source=('qlandkartegt.desktop'
        'qlandkartegt.menu'
        'QLandkarteGT::svn+https://qlandkartegt.svn.sourceforge.net/svnroot/qlandkartegt/QLandkarteGT/trunk')
provides=('qlandkartegt')
replaces=('qlandkarte')
conflicts=('qlandkartegt')

_svnmod="QLandkarteGT"

pkgver()
{
  cd ${srcdir}/$_svnmod
  svnversion | tr -d [A-z]
}

build()
{
    cd ${srcdir}

    # get the sources
    #msg "Connecting to $_svntrunk ..."
    #if [ -d $_svnmod/.svn ]; then
	#(cd $_svnmod && svn up -r $pkgver)
    #else
	#svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
    #fi
    #msg "SVN checkout done or server timeout"

    rm -rf build
    mkdir -p build
    cd build

    cmake -DCMAKE_INSTALL_PREFIX=/usr ${srcdir}/$_svnmod
    make
}

package()
{
    cd ${srcdir}/build

    make DESTDIR=${pkgdir} install

    install -D -m 755 ${srcdir}/$_svnmod/src/icons/orig.backGlobe128x128.png ${pkgdir}/usr/share/pixmaps/qlandkartegt.png
    install -D -m 755 ${srcdir}/qlandkartegt.desktop ${pkgdir}/usr/share/applications/qlandkartegt.desktop
    install -D -m 755 ${srcdir}/qlandkartegt.menu ${pkgdir}/usr/share/menu/qlandkartegt.menu
}

md5sums=('4c543731080f1c7957c7900a0d735c9b'
         'b82cab9c878d0d090b12e84cdbdb1705'
         'SKIP')
