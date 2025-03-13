# Maintainer: m4teo  <m4teo@gmail.com>

pkgname=core-bspwm
pkgver=1.0
pkgrel=2
pkgdesc="Bspwm Configurations for corelinux"
arch=('any')
url="https://github.com/haxorg-ux/core-bspwm"
license=('GPL3')
depends=('bspwm' 'sxhkd' 'feh' 
		'polybar' 'rofi' 'dunst'
)
optdepends=('alacritty: default terminal emulator'
			'kitty: secondary terminal emulator'
			'thunar: default file manager'
			'geany: default text editor'
			'ffmpeg: complete solution to record, convert and stream audio and video, used in screenrecord scripts'
			'xclip: command line interface to the X11 clipboard'
)
options=(!strip !emptydirs)
install="${pkgname}.install"

prepare() {
	cp -af ../files/. "$srcdir"
}

package() {
	local _skeldir="$pkgdir"/etc/skel
	local _configdir="$_skeldir"/.config
	local _wmdir="$_configdir"/bspwm

	mkdir -p "$_skeldir" && mkdir -p "$_configdir" && mkdir -p "$_wmdir"

	# Copy window manager configs
	cp -r "$srcdir"/alacritty 				"$_wmdir"
  cp -r "$srcdir"/polybar 					"$_wmdir"
	
	install -Dm 755 bspwmrc   				"$_wmdir"/bspwmrc
	install -Dm 644 dunstrc   				"$_wmdir"/dunstrc
	install -Dm 644 sxhkdrc					"$_wmdir"/sxhkdrc

	# Make executable
	chmod +x "$_wmdir"/polybar/launch.sh

}
