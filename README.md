# My Manjaro i3 Installation Guide

This guide is intended to reinstall Manjaro i3 asap for my own purposes.
As always, the best guide is the official Arch Linux wiki.

- **Boot** into live USB with **proprietary drivers** enabled.
- My Dell **keyboard** is French Macintosh.
- Enable firewall gui **gufw**:
```
   sudo systemctl enable ufw
   sudo ufw enable
   sudo gufw
```
- Enable TRIM for **SSD**:
```
   sudo systemctl enable fstrim.timer
   sudo systemctl start fstrim.timer
```
- Increase **swapfile size** if the installation was done automatically:
```bash
   sudo swapoff -a ## turn off all swap processes
   sudo dd if=/dev/zero of=/swapfile bs=1G count=16 ## increasing swap to 16 GB
   sudo chmod 600 /swapfile ## Set right permissions (avoid a vulnerability)
   sudo mkswap /swapfile ## make swap
   sudo swapon /swapfile ## activate swap
   grep SwapTotal /proc/meminfo ## OR just htop to see the amount of swap available
```
- **Pamac-manager** gui: enable AUR
                         choose local download servers e.g. Netherlands.
- **Manjaro-settings-manager** gui: add Turkish to locale, install language packages.    
                                    install LTS kernel.    
                                    sync time and date.    
                                    check if all proprietary drivers installed.    
- **Package installations**:
```bash
   sudo pacman -S firefox leafpad mpv code libreoffice-fresh atom kdenlive    
   obs-studio pencil2d signal-desktop telegram-desktop discord    
   firefox-developer-edition tor filezilla  youtube-dl ffmpeg calibre zathura    
   kdeconnect meld uget
```
```bash
   yay -S timeshift sublime-text stacer kite    
   postman-bin boostnote-bin simplenote-electron-bin slack-desktop    
   session-desktop-appimage foxitreader protonvpn librewolf-bin redshift    
   pfetch tixati playerctl alttab-git spotify insomnia-bin
```
- Add **split toggle** in i.3/config where it refers to opening a new terminal.
- **timeshift-launcher** gui: make a system backup.
- Configure **git**:
```bash
   git config --global user.name "Name Surname"
   git config --global user.email "email@email.com"
```
- Add **fonts**:
```bash
   sudo pacman -S ttf-jetbrains-mono ttf-ubuntu-font-family
```
```bash
   yay -S nerd-fonts-complete ttf-ms-fonts ttf-font-awesome-4 ttf-font-icons ttf-ionicos 
```
      My favourite font is Agave Nerd Fonts, which can be set by lxappearance gui.
- working with **bash**:
   I prefer to use bash instead of zsh or fish.    
   **fzf** is the fuzzy match command in this matter.    
   **stow** is the symlink management tool.
   **autojump** enables access to files with the command j
```bash
   sudo pacman -S bash-completion stow fzf
```
   
```bash
   yay -S autojump
```
- Install plugins for VS Code (Code-OSS): Auto Rename Tag, Bracket Pair Colonizer 2, ES7     
     React/Redux/GraphQL/React-Native snippets (configure),Indent-rainbow, Live Server,MDX,    
     Prettier (configure), DotENV

- Install **webstorm** through **jetbrains-toolbox**: (add plugins for VS Code too)    
  In Linux, add the full path for the right version of Chrome in browsers settings in Webstorm:   
  /Usr/bin/google-chrome-stable    
  Install  jetbrains and react dev tools add-ons on Firefox and Chrome    
  Install themes e.g. Dracula-Colorful, Material UI light,Material Design Dark Theme,      
  Xcode, nightfall, Atom Material Icons, Quokka, kite    
  Install plugins kite, wakatime, rainbow-indent, rainbow…    
- Configure **wakatime** API on VS Code and Webstorm
- Disable system **beep**:
```bash
   sudo rmmod pcspkr #to disable the pc speaker kernel module
   sudo vim /etc/modprobe.d/nobeep.conf ## write the following in it
   blacklist pcspkr # Do not load the 'pcspkr' module on boot
```
- Configure **kite** by running in a terminal:
```bash
   /opt/kite/kite-installer install
```
- Configure **alttab-git** by adding to the end of .i3/config:
```bash
   exec --no-startup-id alttab -fg "#d58681" -bg "#4a4a4a" -frame "#eb564d" -t 128x150 -i 127x64
```
- **Reduce swappiness** by creating the following script:
```bash
   sudo vim /etc/sysctl.d/100-manjaro.conf
```
      Write the following in it:
```bash
   vm.swappiness=10
```
- Open **redshift** and click to auto-start

- Install **nvm** from the official Github curl code on https://github.com/nvm-sh/nvm    
  Use npm or yarn as packaage managers for JavaScript
- Use containers instead of virtual machines via **podman/docker**:
```bash
   sudo pacman -S docker podman podman-docker cockpit-podman
```    
      Configure podman following the Arch wiki
- Make a system backup after all the steps on **timeshift**


## Notes:
- **protonVPN** works out of the box after installation without extra config.
- **TLP** is already installed for laptops.
- **Tap-to-click** works out of the box for the touchpad.
- Media buttons like play and pause work after installing **playerctl** without extra config.
- Screen brightness buttons and volume buttons just work out of the box.
