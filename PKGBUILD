# Maintainer: Mister.Bubbles <http://crbserver.net>
# Contributor: daemonTutorials <http://www.daemon-tuts.de>
pkgname=tibia
pkgver=10.78
pkgrel=1
pkgdesc="A free 2D online role playing game."
arch=('i686' 'x86_64')
url="http://www.tibia.com/"
license=('custom:"CipSoft"')
[ "$CARCH" = "i686" ] && depends=('libxdamage' 'mesa')
[ "$CARCH" = "x86_64" ] && depends=('lib32-libxdamage' 'lib32-glu' 'lib32-libxcursor' 'lib32-mesa')
source=(http://static.tibia.com/download/tibia${pkgver/./}.tgz \
	tibia.desktop \
	tibia.png \
	tibia.sh)
sha256sums=('5d9d2425f43d7568f22bb7ecaf6d71bcfd3542ba97a235ae0b76a1f8258afe20'
            '8136fd161e2355a066d83464e9a41c02d61a3a1ee8fe0134480114e1f6eacf2c'
            '4945e47edfdd9b266721d659b6021dc6887204ee293659fde096ac40ee7d0daf'
            '9c4729e7bb982baeb7f7168dbfecc0e051054a617d1ca5ded205adb5cd285045')

build() {
  cd ${srcdir}/Tibia

}

package() {
  cd ${srcdir}/Tibia
  install -d ${pkgdir}/usr/share/{applications,pixmaps,tibia} \
	     ${pkgdir}/usr/bin || return 1

  rm -rf ${srcdir}/Tibia/{libc6,*.sh}
  
  if [ "$CARCH" = "x86_64" ]; then
    install -d ${pkgdir}/usr/share/${pkgname}/libc6 || return 1
    ln -s /usr/lib32/ld-* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libanl* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libBrokenLocale* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libc-*,libc.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libcidn* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libcrypt* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libdl-*,libdl.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libm-*,libm.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libmemusage* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libnsl-*,libnsl.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libnss_* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libpcprofile* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libpthread* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libresolv* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{librt-*,librt.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libSegFault ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/libthread_db* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
    ln -s /usr/lib32/{libutil-*,libutil.*} ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1

    ln -s /usr/lib32/libXdamage* ${pkgdir}/usr/share/${pkgname}/libc6/ || return 1
  fi

  install -m755 ${startdir}/tibia.sh ${pkgdir}/usr/bin/tibia || return 1
  install -m755 Tibia ${pkgdir}/usr/share/tibia/ || return 1
  install -m644 {*.dat,*.pic,*.spr,Patch,Showerror} ${pkgdir}/usr/share/tibia/ || return 1

  install -m644 ${startdir}/tibia.desktop ${pkgdir}/usr/share/applications/ || return 1
  install -m644 ${startdir}/tibia.png ${pkgdir}/usr/share/pixmaps/ || return 1
  install -m644 Tibia.xpm ${pkgdir}/usr/share/pixmaps/tibia.xpm || return 1
}
