### Project only accepting patches
This project is not actively developed but *will* accept PRs

# Archlinux U Install

Install and configure archlinux has never been easier!

You can try it first with a `virtualbox`

## Prerequisites

- A working internet connection
- Logged in as 'root'

## How to get it
### With git
- Increase cowspace partition: `mount -o remount,size=2G /run/archiso/cowspace`
- 修改/etc/pacman.d/mirrorlist，使用国内镜像，加快速度
    - wget https://griffenliu.github.io/aui/mirrors.sh
    - chmod a+x mirrors.sh
    - mirrors.sh
- Get list of packages and install git: `pacman -Sy git`
- get the script: `git clone https://github.com/griffenliu/aui.git`

### Without git
- get the script: ` wget https://github.com/helmuthdu/aui/tarball/master -O - | tar xz`
    - an alternate URL (for less typing (github shorten)) is ` https://git.io/vS1GH -O - | tar xz`
    - an alternate URL (for less typing) is ` wget http://bit.ly/NoUPC6 -O - | tar xz`
    - super short `wget ow.ly/wnFgh -O aui.zip`

## How to use
- FIFO [system base]: `cd <dir> && ./fifo`
- LILO [the rest...]: `cd <dir> && ./lilo`

## 磁盘格式化
```
# 新手版
$ parted /dev/sda( *注意选择自己的安装磁盘* )
  mklabel msdos
  mkpart primary ext4 1M 100M
  set 1 boot on
  mkpart primary linux-swap 100M 1.1G
  mkpart primary ext4 1.1G -1
  p
  q
  
# 升级版
$ parted /dev/sda
  mklabel msdos
  mkpart primary ext4 1M 100M   # 这里如果是独立系统100M足够了，但是如果是多内核或者多系统，则需要扩大空间为200M-500M
  set 1 boot on
  mkpart primary linux-swap 100M 2.1G    # 交换空间要按照内存大小设置，如果内存小于等于2G，则设置为两倍，否则设置为内存大小
  mkpart primary ext4 2.1G 15.1G         # 根目录 / 一般设置为10-15G
  mkpart primary ext4 15.1G -1           # /home目录
```

## FIFO SCRIPT
- Configure keymap
- Select editor
- Automatic configure mirrorlist
- Create partition
- Format device
- Install system base
- Configure fstab
- Configure hostname
- Configure timezone
- Configure hardware clock
- Configure locale
- Configure mkinitcpio
- Install/Configure bootloader
- Configure mirrorlist
- Configure root password

## LILO SCRIPT
- Backup all modified files
- Install additional repositories
- Create and configure new user
- Install and configure sudo
- Automatic enable services in systemd
- Install an AUR Helper [yaourt, packer, pacaur]
- Install base system
- Install systemd
- Install Preload
- Install Zram
- Install Xorg
- Install GPU Drivers
- Install CUPS
- Install Additional wireless/bluetooth firmwares
- Ensuring access to GIT through a firewall
- Install DE or WM [Cinnamon, Enlightenment, FluxBox, GNOME, i3, KDE, LXDE, OpenBox, XFCE]
- Install Developement tools [Vim, Emacs, Eclipse...]
- Install Office apps [LibreOffice, GNOME-Office, Latex...]
- Install System tools [Wine, Virtualbox, Grsync, Htop]
- Install Graphics apps [Inkscape, Gimp, Blender, MComix]
- Install Internet apps [Firefox, Google-Chrome, Jdownloader...]
- Install Multimedia apps [Rhythmbox, Clementine, Codecs...]
- Install Games [HoN, World of Padman, Wesnoth...]
- Install Fonts [Liberation, MS-Fonts, Google-webfonts...]
- Install and configure Web Servers
- Many More...

If you like my work, please consider a small Paypal donation at helmuthdu@gmail.com :)
