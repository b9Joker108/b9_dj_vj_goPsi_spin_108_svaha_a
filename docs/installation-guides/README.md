# Installation Guides - Setup Instructions for GNU/Linux

## Overview

Comprehensive installation and configuration instructions for all FOSS video production tools on various GNU/Linux distributions.

## 🐧 Distribution-Specific Guides

### Ubuntu/Debian-Based Systems

#### **System Update and Prerequisites**
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install essential build tools
sudo apt install -y build-essential git cmake pkg-config

# Install common libraries
sudo apt install -y libavcodec-dev libavformat-dev libavutil-dev \
    libswscale-dev libavresample-dev libsdl2-dev libgtk-3-dev
```

### Fedora/RHEL-Based Systems

```bash
# Update system
sudo dnf update -y

# Install development tools
sudo dnf groupinstall -y "Development Tools"

# Enable RPM Fusion repositories
sudo dnf install -y https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install -y https://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

### Arch-Based Systems

```bash
# Update system
sudo pacman -Syu

# Install base development packages
sudo pacman -S base-devel git cmake

# Enable multilib (for 32-bit support)
# Edit /etc/pacman.conf and uncomment [multilib] section
```

## 🎬 Video Editing Software Installation

### Kdenlive

#### **Ubuntu/Debian**
```bash
# Official PPA (latest version)
sudo add-apt-repository ppa:kdenlive/kdenlive-stable
sudo apt update
sudo apt install kdenlive

# Or from default repositories
sudo apt install kdenlive

# AppImage (portable)
wget https://download.kde.org/stable/kdenlive/$(curl -s https://download.kde.org/stable/kdenlive/ | grep -oP 'kdenlive-[0-9.]+.AppImage' | head -1)
chmod +x kdenlive-*.AppImage
./kdenlive-*.AppImage
```

#### **Fedora**
```bash
sudo dnf install kdenlive
```

#### **Arch**
```bash
sudo pacman -S kdenlive
```

#### **Configuration Tips**
- Enable proxy clips for 4K editing: Settings → Configure Kdenlive → Proxy Clips
- GPU acceleration: Settings → Configure Kdenlive → Environment → Processing threads
- Configure cache location on SSD for better performance

---

### DaVinci Resolve

#### **System Requirements**
- RAM: 16GB minimum, 32GB+ recommended
- GPU: OpenCL 1.2 or CUDA 11
- Disk: 50GB+ free space

#### **Installation (All Distros)**
```bash
# Download from BlackmagicDesign website
# Extract the downloaded zip
unzip DaVinci_Resolve_*_Linux.zip

# Run installer
cd DaVinci_Resolve_*_Linux/
sudo ./DaVinci_Resolve_*.sh

# Fix library dependencies if needed
sudo apt install libssl1.1  # Ubuntu/Debian
# Or download libssl1.1 from older release
```

#### **Common Issues and Fixes**
```bash
# If fails to start
# Check logs
cat ~/.local/share/DaVinciResolve/logs/ResolveDebug.txt

# Database fix
rm -rf ~/.local/share/DaVinciResolve/configs/.database*

# Missing libraries (Debian/Ubuntu)
sudo apt install libapr1 libaprutil1 libglu1-mesa libxcb-composite0
```

---

### Shotcut

#### **Ubuntu/Debian**
```bash
# Flatpak (recommended)
flatpak install flathub org.shotcut.Shotcut

# Or download AppImage from website
wget https://github.com/mltframework/shotcut/releases/download/v23.XX.XX/shotcut-linux-x86_64-230XXX.txz
tar xvf shotcut-*.txz
cd Shotcut.app
./shotcut
```

#### **Fedora**
```bash
sudo dnf install shotcut
```

#### **Arch**
```bash
sudo pacman -S shotcut
```

---

### Flowblade

#### **Ubuntu/Debian**
```bash
# From repositories
sudo apt install flowblade

# Or via Flatpak
flatpak install flathub io.github.jliljebl.Flowblade
```

#### **Fedora**
```bash
sudo dnf install flowblade
```

#### **Arch**
```bash
yay -S flowblade  # From AUR
```

---

### Blender

#### **Ubuntu/Debian**
```bash
# Latest version via Snap
sudo snap install blender --classic

# Or download from blender.org
wget https://www.blender.org/download/release/Blender3.X/blender-3.X.X-linux-x64.tar.xz
tar xf blender-*.tar.xz
cd blender-*
./blender
```

#### **Fedora**
```bash
sudo dnf install blender
```

#### **Arch**
```bash
sudo pacman -S blender
```

#### **Configuration**
- Enable GPU rendering: Edit → Preferences → System → Cycles Render Devices
- Install add-ons: Edit → Preferences → Add-ons
- Set up workspaces for video editing

---

### Natron

#### **All Distributions**
```bash
# Download from natrongithub.github.io
wget https://github.com/NatronGitHub/Natron/releases/download/v2.X.X/Natron-2.X.X-Linux-x86_64.tgz
tar xzf Natron-*.tgz
cd Natron-*/
./Natron
```

#### **Install OpenFX Plugins**
```bash
# Create plugins directory
mkdir -p ~/.local/share/OpenFX/Plugins

# Download and install popular plugins
# - openfx-misc
# - openfx-io
# - openfx-arena
```

---

## 🎨 VJ Applications Installation

### Veejay

#### **Ubuntu/Debian**
```bash
# Install dependencies
sudo apt install -y libsdl2-dev libjpeg-dev libavcodec-dev \
    libavformat-dev libavutil-dev libswscale-dev libxml2-dev \
    libfreetype6-dev libfontconfig1-dev libx11-dev

# From source (latest version)
git clone https://github.com/c0ntrol/veejay.git
cd veejay
./autogen.sh
./configure
make
sudo make install
```

#### **Arch**
```bash
yay -S veejay  # From AUR
```

---

### FreeJ

#### **Ubuntu/Debian**
```bash
sudo apt install freej
```

#### **From Source**
```bash
git clone https://github.com/jaromil/FreeJ.git
cd FreeJ
./autogen.sh
./configure
make
sudo make install
```

---

### OBS Studio

#### **Ubuntu/Debian**
```bash
# Official PPA
sudo add-apt-repository ppa:obsproject/obs-studio
sudo apt update
sudo apt install obs-studio

# Or via Flatpak
flatpak install flathub com.obsproject.Studio
```

#### **Fedora**
```bash
sudo dnf install obs-studio
```

#### **Arch**
```bash
sudo pacman -S obs-studio
```

#### **Plugins**
```bash
# Install useful plugins
# - OBS-VirtualCam (v4l2loopback)
# - StreamFX (advanced effects)
# - obs-websocket (remote control)
```

---

### Processing

#### **All Distributions**
```bash
# Download from processing.org
wget https://github.com/processing/processing4/releases/download/processing-XXXX/processing-XXXX-linux-x64.tgz
tar xzf processing-*.tgz
cd processing-*/
./processing
```

#### **Install Video Library**
```
Sketch → Import Library → Manage Libraries → Search "Video"
```

---

### Pure Data + GEM

#### **Ubuntu/Debian**
```bash
# Install Pure Data
sudo apt install puredata puredata-dev puredata-gui

# Install GEM
sudo apt install gem

# Or build GEM from source for latest version
git clone https://github.com/umlaeute/Gem.git
cd Gem
./autogen.sh
./configure
make
sudo make install
```

#### **Fedora**
```bash
sudo dnf install puredata gem
```

#### **Arch**
```bash
sudo pacman -S pd gem
```

---

### KodeLife

#### **All Distributions**
```bash
# Download from hexler.net
wget https://hexler.net/pub/kodelife/kodelife-1.X.X.x86_64.tar.gz
tar xzf kodelife-*.tar.gz
cd KodeLife
./KodeLife
```

---

## 🔧 Supporting Tools Installation

### FFmpeg (Full Build with All Codecs)

#### **Ubuntu/Debian**
```bash
# Basic installation
sudo apt install ffmpeg

# Or compile with all features
sudo apt install -y autoconf automake build-essential cmake git-core \
    libass-dev libfreetype6-dev libgnutls28-dev libmp3lame-dev \
    libsdl2-dev libtool libva-dev libvdpau-dev libvorbis-dev \
    libxcb1-dev libxcb-shm0-dev libxcb-xfixes0-dev meson ninja-build \
    pkg-config texinfo wget yasm zlib1g-dev libunistring-dev \
    libx264-dev libx265-dev libnuma-dev libvpx-dev libfdk-aac-dev \
    libopus-dev libdav1d-dev

# Build from source
git clone https://git.ffmpeg.org/ffmpeg.git
cd ffmpeg
./configure --enable-gpl --enable-nonfree --enable-libx264 \
    --enable-libx265 --enable-libvpx --enable-libfdk-aac \
    --enable-libopus --enable-libdav1d
make -j$(nproc)
sudo make install
```

---

### JACK Audio Connection Kit

#### **Ubuntu/Debian**
```bash
sudo apt install jackd2 qjackctl

# Configure realtime privileges
sudo usermod -aG audio $USER

# Add to /etc/security/limits.conf
echo "@audio   -  rtprio     95" | sudo tee -a /etc/security/limits.conf
echo "@audio   -  memlock    unlimited" | sudo tee -a /etc/security/limits.conf
```

#### **Fedora**
```bash
sudo dnf install jack-audio-connection-kit qjackctl
```

#### **Configuration**
```bash
# Launch QJackCtl
qjackctl

# Settings:
# - Sample Rate: 48000
# - Frames/Period: 256 or 512
# - Periods/Buffer: 2
```

---

### v4l2loopback (Virtual Camera)

#### **Ubuntu/Debian**
```bash
sudo apt install v4l2loopback-dkms

# Load module
sudo modprobe v4l2loopback devices=1 video_nr=10 card_label="VirtualCam" exclusive_caps=1

# Persist on boot
echo "v4l2loopback" | sudo tee -a /etc/modules
```

#### **Fedora**
```bash
sudo dnf install v4l2loopback
sudo modprobe v4l2loopback
```

---

### G'MIC

#### **Ubuntu/Debian**
```bash
sudo apt install gmic gmic-qt gmic-gimp
```

#### **Fedora**
```bash
sudo dnf install gmic gmic-qt
```

#### **Arch**
```bash
sudo pacman -S gmic
```

---

### HandBrake

#### **Ubuntu/Debian**
```bash
# Official PPA
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt update
sudo apt install handbrake-gtk
```

#### **Fedora**
```bash
sudo dnf install handbrake handbrake-gui
```

---

### Audacity

#### **Ubuntu/Debian**
```bash
sudo apt install audacity
```

#### **Latest version via Flatpak**
```bash
flatpak install flathub org.audacityteam.Audacity
```

---

### GIMP & Inkscape

#### **All Distributions**
```bash
# Ubuntu/Debian
sudo apt install gimp inkscape

# Fedora
sudo dnf install gimp inkscape

# Arch
sudo pacman -S gimp inkscape
```

---

## 🎯 Complete VJ Workstation Setup

### Full Installation Script (Ubuntu/Debian)

```bash
#!/bin/bash
# VJ and Video Production Workstation Setup

# Update system
sudo apt update && sudo apt upgrade -y

# Add PPAs
sudo add-apt-repository ppa:kdenlive/kdenlive-stable -y
sudo add-apt-repository ppa:obsproject/obs-studio -y
sudo apt update

# Install editors
sudo apt install kdenlive flowblade shotcut -y

# Install VJ tools
sudo apt install freej obs-studio puredata gem -y

# Install supporting tools
sudo apt install ffmpeg jackd2 qjackctl audacity gimp inkscape -y
sudo apt install gmic gmic-qt v4l2loopback-dkms -y

# Install Blender (Snap)
sudo snap install blender --classic

# User permissions
sudo usermod -aG audio $USER
sudo usermod -aG video $USER

# JACK realtime config
echo "@audio   -  rtprio     95" | sudo tee -a /etc/security/limits.conf
echo "@audio   -  memlock    unlimited" | sudo tee -a /etc/security/limits.conf

# v4l2loopback setup
echo "v4l2loopback" | sudo tee -a /etc/modules
sudo modprobe v4l2loopback devices=2

echo "Installation complete! Please reboot for all changes to take effect."
```

---

## 🔍 Troubleshooting

### Common Issues

#### **Video playback stuttering**
```bash
# Increase cache
# In Kdenlive: Settings → Configure → Playback → Buffer size

# Use proxy editing
# Project Settings → Proxy clips
```

#### **JACK audio issues**
```bash
# If JACK won't start
killall jackd
sudo killall jackdbus

# Restart with QJackCtl
```

#### **GPU rendering not working**
```bash
# Check GPU
lspci | grep VGA

# Install appropriate drivers
# NVIDIA
sudo apt install nvidia-driver-XXX

# AMD
sudo apt install mesa-vulkan-drivers
```

#### **Permission denied errors**
```bash
# Add user to required groups
sudo usermod -aG audio,video,render $USER

# Reboot required
```

---

## 📚 Post-Installation Configuration

### System Optimization

#### **Increase file watchers (for large projects)**
```bash
echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

#### **Optimize swap**
```bash
# Reduce swappiness
echo "vm.swappiness=10" | sudo tee -a /etc/sysctl.conf
sudo sysctl -p
```

#### **Setup scratch disk**
```bash
# Use SSD for cache/temp files
mkdir -p ~/video_cache
# Point applications to use this directory
```

### Color Management

```bash
# Install color profiles
sudo apt install icc-profiles argyll

# For DaVinci Resolve
# Use ACES color space when possible
```

---

## 🔗 Additional Resources

- [VJ Applications](../vj-applications/) - Software overview
- [Video Editing](../video-editing/) - Editor comparison
- [Practical Workflows](../practical-workflows/) - Usage examples
- [Learning Resources](../learning-resources/) - Tutorials

---

## 📝 Notes

- Always check official documentation for latest installation methods
- Some software may require system reboot after installation
- GPU drivers are critical for performance
- Backup your system before major installations
- Test installations with sample projects

---

*Keep your system updated and regularly check for software updates to ensure optimal performance and security.*
