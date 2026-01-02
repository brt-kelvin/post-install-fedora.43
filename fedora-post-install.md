# 🐧 Fedora – Pós-instalação & Setup Inicial

Guia de configuração inicial do Fedora com codecs, remoção de apps padrão,
instalação de ferramentas e personalização do terminal.

---

## 🔄 Atualização do Sistema

sudo dnf update
sudo dnf upgrade

---

## 📦 Ativar RPM Fusion (Free & Non-Free)

sudo dnf install \
https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

sudo dnf update
sudo dnf upgrade

---

## 🎵 Codecs Multimídia

sudo dnf4 group install multimedia
sudo dnf remove ffmpeg-free
sudo dnf install ffmpeg
sudo dnf group install sound-and-video

---

## 🧹 Remover Aplicativos Padrão

sudo dnf remove \
gnome-weather \
gnome-maps \
libreoffice* \
gnome-tour \
firefox \
showtime

---

## 📦 Suporte a AppImage

sudo dnf install fuse
flatpak install flathub it.mijorus.gearlever

---

## 💻 Instalação de Aplicativos

### 📝 Visual Studio Code

sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

echo -e "[code]
name=Visual Studio Code
baseurl=https://packages.microsoft.com/yumrepos/vscode
enabled=1
autorefresh=1
type=rpm-md
gpgcheck=1
gpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null

dnf check-update
sudo dnf install code

---

### 🛠️ Utilitários do Sistema

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

---

## 📦 Aplicativos Flatpak

flatpak install flathub \
org.mozilla.firefox \
com.jetbrains.PyCharm-Professional \
org.onlyoffice.desktopeditors \
org.gnome.Extensions \
com.mattjakeman.ExtensionManager \
md.obsidian.Obsidian

---

## 🧽 Limpeza do Sistema

sudo dnf autoremove

---

## 🌐 Downloads Manuais

VirtualBox: https://www.virtualbox.org/wiki/Linux_Downloads
JetBrains Mono: https://www.jetbrains.com/lp/mono/

---

## 🐟 Fish + Starship

curl -sS https://starship.rs/install.sh | sh

sudo dnf copr enable atim/starship
sudo dnf install starship

Adicionar em ~/.config/fish/config.fish:
starship init fish | source
