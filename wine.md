# Eroge Wine Guide

## WineHQ

You can use stable from Ubuntu/Pop repo with no problems, it's fine if WineHQ doesn't have the stable release available.

Follow the steps below if you want to use an newer version. (This is based on Ubunt/Pop 22.04, from [here](https://wiki.winehq.org/Ubuntu))

> sudo dpkg --add-architecture i386 

> sudo mkdir -pm755 /etc/apt/keyrings

> sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key

> sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources

> sudo apt update

> sudo apt install --install-recommends winehq-stable

Install some needed packages after wine:

> sudo apt install libgnutls30:i386 libldap-2.4-2:i386 libgpg-error0:i386 libxml2:i386 libasound2-plugins:i386 libsdl2-2.0-0:i386 libfreetype6:i386 libdbus-1-3:i386 libsqlite3-0:i386 libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386 libgstreamer-plugins-bad1.0-0:i386 libgudev-1.0-0:i386 ocl-icd-dev:i386 

Install winetricks: 

> wget https://raw.githubusercontent.com/Winetricks/winetricks/master/src/winetricks

> chmod +x winetricks

> sudo cp winetricks /usr/bin

Install CDEmu

> sudo add-apt-repository ppa:cdemu/ppa -y

> sudo apt update

> sudo apt install vhba-dkms 

If you want an GUI for cdemu, you can use gCDEmu (package gcdemu).

## Configure Prefix

> WINEPREFIX=~/.winevn WINEARCH=win32 wineboot

> sudo winetricks --self-update

> WINEPREFIX=~/.winevn winetricks ffdshow quartz_feb2010 wmp10 d3dx9 dotnet35 vcrun2003 vcrun2005 vcrun2008 vcrun2010 vcrun2012 vcrun2013 vcrun2015

> WINEPREFIX=~/.winevn winetricks dxvk

> WINEPREFIX=~/.winevn winetricks lavfilters

> WINEPREFIX=~/.winevn winetricks alldlls=default

You can revert using native DLLs running (undo the command above): 

> WINEPREFIX=~/.winevn winetricks alldlls=builtin

For fonts, use the fonts zip in this repo and move the files inside to `~/.winevn/drive_c/windows/Fonts`

## Instaling Games

Use cdemu to mount the disc and run `LC_ALL="ja_JP.UTF-8" TZ="Asia/Tokyo" WINEPREFIX=~/.winevn wine <setup>.exe`.

## Running games 

You can use Lutris with this prefix but I personally prefer creating a simple shellscript. I've added my Sakura no Uta script in the files as reference.

## Locale

Needless to say, you need to add ja_JP locale beforehand. 

For Shift-JIS: 

1. Extract the sjis zip in the repo
1. `cd /path/to/ja_JP.sjis`
1. `localedef -i ja_JP -f SHIFT_JIS ./ja_JP.sjis --no-warnings=ascii`
1. `sed -i '/ja_JP.UTF-8 UTF-8/a ja_JP.SJIS SHIFT_JIS  ' /etc/locale.gen`
1. `locale-gen`

Then use `LC_ALL` with ` ja_JP.sjis` for the games you need it. 

---

If you don't understand what each command does here, follow this [guide](https://learnjapanese.moe/vn-linux/) instead. This is basically a backup of it. 

