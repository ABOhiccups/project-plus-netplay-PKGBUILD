# Maintainer: ABOhiccups <info@abohiccups.com>
pkgname=project-plus-netplay
pkgver='v2.5.2'
_tagname='2.5.2'
pkgrel='1'
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
_sd="sd.tar.gz"
source=(
	"$_package::$_url/download/$pkgver/$_package"
	"$_launcher::$_url/download/$pkgver/$_launcher"
	"$_sd::$_url/download/$pkgver/$_sd"
)
sha256sums=('a734b439e063f301e79d8acbfb8c448f0e998cee557685d4db7f25209a68da83' '1b9dce2fb0eac3ad8cc809826b3b6bfd4ce30dbfc394eaa586e35dcd356fd189' '121d08f8fcbf2fc24d5b48481f387398f24be30de3eb66fb510cb9f5a67f4657')

prepare() {
	chmod +x "$srcdir/$_package"
	$srcdir/$_package --appimage-extract
}

package() {
	install -Dm755 "$_package" "$pkgdir/usr/bin/$pkgname"
	install -Dm644 "squashfs-root/usr/share/icons/hicolor/512x512/apps/ishiiruka.png" "$pkgdir/usr/share/pixmaps/$pkgname.png"
	install -dm644 "$pkgdir/usr/share/applications"
	printf "[Desktop Entry]\nVersion=${pkgver:1}\nName=Project+ Netplay\nComment=A Mod of Super Smash Bros. Brawl with Netplay.\nPath=/usr/bin\nExec=project-plus-netplay\nIcon=project-plus-netplay\nType=Application\nCategories=Game\nKeywords=project+;brawl;netplay\n" > "$pkgdir/usr/share/applications/$pkgname.desktop"
	install -d "$pkgdir/$HOME/Documents/Project+ Netplay/Games"
	touch "/$pkgdir/$HOME/Documents/Project+ Netplay/Games/Place Brawl ISO here"
	cp -R "Launcher" "$pkgdir/$HOME/Documents/Project+ Netplay"
	chown -R "$USER" "$pkgdir/$HOME/Documents/Project+ Netplay"
	install -D "sd.raw" "$pkgdir/$HOME/.local/share/FasterPPlus/Wii/sd.raw"
	chown -R "$USER" "$pkgdir/$HOME/.local/share/FasterPPlus"
}
