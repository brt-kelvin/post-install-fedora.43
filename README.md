# 🐧 Fedora – Post-installation & Initial Setup

Initial Fedora setup guide with multimedia codecs, removal of default apps,
tool installation, and terminal customization.

---

## 🔄 System Update

```bash
sudo dnf update
sudo dnf upgrade
```

---

## 📦 Enable RPM Fusion (Free & Non-Free)

```bash
sudo dnf install \
https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

```bash
sudo dnf update
sudo dnf upgrade
```

---

## 🎵 Multimedia Codecs

```bash
sudo dnf4 group install multimedia
sudo dnf remove ffmpeg-free
sudo dnf install ffmpeg
sudo dnf group install sound-and-video
```

---

## 🧹 Remove Default Applications

```bash
sudo dnf remove \
gnome-weather \
gnome-maps \
libreoffice* \
gnome-tour \
firefox \
showtime
```

---

## 📦 AppImage Support

```bash
sudo dnf install fuse
flatpak install flathub it.mijorus.gearlever
```

---

## 💻 Application Installation

### 📝 Visual Studio Code

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```

```bash
echo -e "[code]
name=Visual Studio Code
baseurl=https://packages.microsoft.com/yumrepos/vscode
enabled=1
autorefresh=1
type=rpm-md
gpgcheck=1
gpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null
```

```bash
dnf check-update
sudo dnf install code
```

---

### 🛠️ System Utilities

```bash
sudo dnf install \
unzip \
p7zip \
p7zip-plugins \
unrar \
git \
curl \
wget \
mpv \
gimp \
xournalpp \
fish \
chromium \
discord \
gnome-tweaks
```

---

## 📦 Flatpak Applications

```bash
flatpak install flathub \
org.mozilla.firefox \
com.jetbrains.PyCharm-Professional \
org.onlyoffice.desktopeditors \
org.gnome.Extensions \
com.mattjakeman.ExtensionManager \
md.obsidian.Obsidian
```

---

## 🧽 System Cleanup

```bash
sudo dnf autoremove
```

---

## 🌐 Manual Downloads

- **VirtualBox**  
  https://www.virtualbox.org/wiki/Linux_Downloads

- **JetBrains Mono Font**  
  https://www.jetbrains.com/lp/mono/

---

## 🐟 Fish Shell + Starship Prompt

```bash
curl -sS https://starship.rs/install.sh | sh
```

```bash
sudo dnf copr enable atim/starship
sudo dnf install starship
```

Edit the following file:

```bash
~/.config/fish/config.fish
```

Add at the end:

```fish
starship init fish | source
```

---

## ✅ Done

Your Fedora system is now ready 🚀
