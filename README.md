# A Simple BSPWM Setup

Much of this is blatantly plagarized from various r/unixporn dotfile repos. If I could remember which ones I used I'd credit them, but I don't, so just be aware most of this isn't my work.

This also isn't what I use anymore, I moved to another distro.

## Installation (assumes Ubuntu 21.10 or similar)

Install the required packages:

```bash
sudo apt update && sudo apt upgrade
sudo apt install bspwm kitty rofi picom polybar nitrogen
```

Clone this repo and copy all `.config` folders into `~/.config/`. Make bspwmrc and launch.sh executable

```bash
chmod +x ~/.config/bspwm/bspwmrc
chmod +x ~/.config/polybar/launch.sh
```

Install RobotoMono and Iosevka from [here](https://github.com/ryanoasis/nerd-fonts/releases/latest) by unzipping and copying to `/usr/local/share/fonts`, and do `fc-cache -f -v` after (or restart).

Restart, use settings cog on login page to switch to BSPWM

To get a desktop background, download an image to some directory, and then do `nitrogen /path/to/image/directory` and select the image. Whatever you choose will be kept on future restarts.

To get the lockscreen to work first we need to compile `i3lock-color`. Download and unzip the latest source code release from [the release page](https://github.com/Raymo111/i3lock-color/releases/), and install the required dependencies (or clone it, but that may include bugs).

```bash
sudo apt install imagemagick autoconf gcc make pkg-config libpam0g-dev libcairo2-dev libfontconfig1-dev libxcb-composite0-dev libev-dev libx11-xcb-dev libxcb-xkb-dev libxcb-xinerama0-dev libxcb-randr0-dev libxcb-image0-dev libxcb-util-dev libxcb-xrm-dev libxcb-xtest0-dev libxkbcommon-dev libxkbcommon-x11-dev libjpeg-dev
```

Then, cd into the repo and install

```bash
cd i3lock-color
./install-i3lock-color.sh
```

Then, clone the [betterlockscreen repo](https://github.com/betterlockscreen/betterlockscreen), then do

```bash
cd betterlockscreen
chmod +x install.sh
sudo ./install.sh system
```

(Change "system" to "user" if you only want it installed for you. I've had issues with that working though, so explore at your own risk.)

Then, set the image with

```bash
betterlockscreen -u /path/to/image
```

Done!
