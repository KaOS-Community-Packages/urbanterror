pkgname=urbanterror
pkgver=4.2.020
pkgrel=1
pkgdesc="A team-based tactical shooter based on the Quake 3 Engine"
arch=('x86_64')
url="http://www.urbanterror.info"
license=('GPL2')
depends=('sdl' 'openal' 'curl')
makedepends=('mesa')
source=("http://up.barbatos.fr/urt/UrbanTerror42_full020.zip"
        "urbanterror.sh"
        "urbanterror-server.sh"
        "urbanterror.desktop"
        "urbanterror.png")
md5sums=('e17a0708c8682e727a07f09ca5408f0c'
         '7812ece92ab71986ef038b3291adc412'
         'fbd3059497cf68769c0cbf02545c6bec'
         '08a99f4d7ad63024bc886e118ddcbc0f'
         'f9a57d898df73f43c6a85c8d8cc455ba')

package() {
  mkdir -p $pkgdir/opt/urbanterror
  cp -r $srcdir/UrbanTerror42/q3ut4 $pkgdir/opt/urbanterror/q3ut4
  install -d $pkgdir/opt/urbanterror

  cd $pkgdir/opt/urbanterror

  # Copy binaries.
  install -m755 $srcdir/UrbanTerror42/Quake3-UrT.x86_64 urbanterror
  install -m755 $srcdir/UrbanTerror42/Quake3-UrT-Ded.x86_64 urbanterror-ded

  # Copy desktop launcher.
  install -Dm644 $srcdir/UrbanTerror42/q3ut4/readme42.txt $pkgdir/usr/share/licenses/$pkgname/LICENSE
  install -Dm644 $srcdir/urbanterror.desktop $pkgdir/usr/share/applications/urbanterror.desktop
  install -Dm644 $srcdir/urbanterror.png $pkgdir/usr/share/pixmaps/urbanterror.png

  # Copy launch scripts.
  install -Dm755 $srcdir/urbanterror.sh $pkgdir/usr/bin/urbanterror
  install -Dm755 $srcdir/urbanterror-server.sh $pkgdir/usr/bin/urbanterror-server
  echo -e "\nseta cl_cURLLib \"/usr/lib/libcurl.so.4\"" >> $pkgdir/opt/urbanterror/q3ut4/autoexec.cfg
}
