# Maintainer: ABOhiccups <https://twitter.com/ABOhiccups>
pkgname=project-plus-netplay
_tagname='2.29'
pkgver=2.29
pkgrel=3
pkgdesc="A Mod of Super Smash Bros. Brawl with Netplay."
arch=('x86_64')
url="https://projectplusgame.com/"
license=('GPL')
depends=('alsa-lib' 'bluez-libs' 'cairo' 'curl' 'enet' 'ffmpeg' 'gcc-libs' 'gdk-pixbuf2' 'glib2' 'glibc' 'gtk2' 'hidapi' 'libevdev' 'libpng' 'libpulse' 'libsm' 'libusb' 'libx11' 'libxi' 'libxrandr' 'libxxf86vm' 'lzo' 'mbedtls' 'miniupnpc' 'official-gamecube-controller-adapter-rules' 'pango' 'sfml' 'systemd-libs' 'zlib')
makedepends=('cmake' 'git' 'qt5-base')
optdepends=('pulseaudio: PulseAudio backend')
options=('!strip')
_url="https://github.com/jlambert360/FPM-AppImage/releases"
_package="Faster_Project_Plus-x86-64.AppImage"
_launcher="Launcher.tar.gz"
_sd="ProjectPlusSd$_tagname.tar.gz"
source=(
	"$_package::$_url/download/v$_tagname/$_package"
	"$_launcher::$_url/download/v$_tagname/$_launcher"
	"$_sd::$_url/download/v$_tagname/$_sd"
)
sha512sums=('0b6e30875e1afd735e62022180cf87f801ac12740539e7363b1fd6379341a7df9c6ecc8731142011d206c43b005e23fba530b3404d36a72e6181af10f4f06e7a'
	'8f392f9ea39bc61b4afb704ddc20e29a603ce6c3947b227ec095f68e541c298dd4cc7cff30454ed3c3562206dff2d5399eb241a40bc0ea6f09dda3bbaf434d6e'
	'b21ebcdd30c26a24841201b4264a2a5a4cab1800c3a887a99a9320db7700ef6a0a37b62ab7ae95e1789797dff93e33c0f30968a584bf9b19044f60f51d21f5b0')

prepare() {
	chmod +x "$srcdir/$_package"
	$srcdir/$_package --appimage-extract
}

package() {
	install -Dm755 "$_package" "$pkgdir/usr/bin/$pkgname"
	install -Dm644 "squashfs-root/usr/share/icons/hicolor/512x512/apps/ishiiruka.png" "$pkgdir/usr/share/pixmaps/$pkgname.png"
	install -dm644 "$pkgdir/usr/share/applications"
	printf "[Desktop Entry]\nVersion=$_tagname\nName=Project+ Netplay\nComment=A Mod of Super Smash Bros. Brawl with Netplay.\nPath=/usr/bin\nExec=project-plus-netplay\nIcon=project-plus-netplay\nType=Application\nCategories=Game\nKeywords=project+;brawl;netplay\n" > "$pkgdir/usr/share/applications/$pkgname.desktop"
	install -d "$pkgdir/$HOME/Documents/Project+ Netplay/Games"
	touch "/$pkgdir/$HOME/Documents/Project+ Netplay/Games/Place Brawl ISO here"
	cp -R "Launcher" "$pkgdir/$HOME/Documents/Project+ Netplay"
	chown -R "$USER" "$pkgdir/$HOME/Documents/Project+ Netplay"
	install -D "ProjectPlusSd$_tagname.raw" "$pkgdir/$HOME/.local/share/FasterPPlus/Wii/sd.raw"
	chown -R "$USER" "$pkgdir/$HOME/.local/share/FasterPPlus"
}