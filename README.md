# My i3 Manjaro Installation Guide

This is intended only to reinstall Manjaro i3 asap for my own purposes. Feel free to use!

- **boot** into live USB with **proprietary drivers** enabled
- Dell **keyboard** is French Macintosh
- enable firewall gui **gufw**
- increase **swapfile size**
```bash
   sudo swapoff -a ## turn off all swap processes
   sudo dd if=/dev/zero of=/swapfile bs=1G count=16 ## increasing swap to 16 GB
   sudo chmod 600 /swapfile ## Set right permissions (avoid a vulnerability)
   sudo mkswap /swapfile ## make swap
   sudo swapon /swapfile ## activate swap
   grep SwapTotal /proc/meminfo ## OR just htop to see the amount of swap available
```
- **pamac-manager** gui: enable AUR
                    choose local download servers e.g. Netherlands
- **manjaro-settings-manager** gui: add Turkish to locale, install language packages
                                    install LTS kernel
                                    sync time and date
                                    check if all proprietary drivers installed
- **package installations**:
 ```bash
    sudo pacman -S firefox leafpad mpv code libreoffice-fresh atom kdenlive    
    obs-studio pencil2d signal-desktop telegram-desktop discord    
    firefox-developer-edition tor filezilla  youtube-dl ffmpeg calibre zathura    
    kdeconnect meld uget
 ```
 - **package installations**:
```bash
    yay -S timeshift geoclue2 skypeforlinux-stable-bin sublime-text stacer kite    
    postman-bin boostnote-bin simplenote-electron-bin slack-desktop    
    session-desktop-appimage foxitreader protonvpn librewolf-bin redshift-minimal    
    pfetch tixati playerctl alttab-git
```
- add **split toggle** in i.3/config where it refers to opening a new terminal 
- **timeshift-launcher** gui: make a system backup
- configure **git**:
```bash
     git config --global user.name "Name Surname
     git config --global user.email "email@email.com"
```
- add **fonts**:
```bash
     sudo pacman -S ttf-jetbrains-mono ttf-ubuntu-font-family
```
```bash
      yay -S nerd-fonts-complete ttf-ms-fonts ttf-font-awesome-4 ttf-font-icons ttf-ionicos 
```
- install **webstorm** through **jetbrains-toolbox**: (add plugins for vs code too)    
      install  jetbrains and react dev tools add-ons on Firefox and Chrome    
      install themes e.g. Dracula-Colorful, Material UI light,Material Design Dark Theme,      
      Xcode, nightfall, Atom Material Icons, Quokka, kite    
      install plugins kite, wakatime, rainbow-indent, rainbow…    
- configure **wakatime** API on VS Code and Webstorm
- disable system **beep**:
```bash
      rmmod pcspkr #to disable the pc speaker kernel module
      sudo nano /etc/modprobe.d/nobeep.conf ## write the following in it
      blacklist pcspkr # Do not load the 'pcspkr' module on boot
```
- configure **kite** by running in a terminal:
```bash
      /opt/kite/kite-installer install
```
- configure **alttab-git** by adding to the end of .i3/config:
```bash
      exec --no-startup-id alttab -fg "#d58681" -bg "#4a4a4a" -frame "#eb564d" -t 128x150 -i 127x64
```
- configure **redshift**:
    Change owner of the file to the user
```bash
      chown user:user /etc/geoclue/geoclue.conf # change user name
```      
    Add the following to the end of /etc/geoclue/geoclue.conf
       
```bash
      # ...
      [redshift]
      allowed=true
      system=false
      users= # this is empty
```
    Change owner of the file back to root

```bash
      chown root:root /etc/geoclue/geoclue.conf
```
    Add to .i3/config
```bash
      exec --no-startup-id /usr/lib/geoclue-2.0/demos/agent 
      exec --no-startup-id redshift-gtk # or redshift name from Arch wiki    
```
- **Reduce swappiness** by creating the following script:
```bash
sudo vim /etc/sysctl.d/100-manjaro.conf
```
Write the following in it/
````bash
vm.swappiness=10
```

## Optional:
- install **cockpit, packagekit, docker and podman**

## Notes:
- **protonVPN** works out of the box without interfering
- **TLP** is already installed
- **Tap-to-click** works out of the box
