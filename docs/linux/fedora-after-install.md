# Things I Do After Installing Fedora Workstation:


## Updating the system:

```bash
sudo dnf upgrade --refresh -y
```

## Installing some useful missing apps:

### [GNOME Tweaks](https://gitlab.gnome.org/GNOME/gnome-tweaks) to add *maximize* and *minimize* buttons to the apps window:

```bash
 sudo dnf install gnome-tweaks
```

!!! tip "How to:"
    open  Gnome Tweaks, then go to *Windows* --> *Titlebar Buttons*, and switch on **Maximize** and **Minimize**.

### [Adw-gtk3](https://github.com/lassekongo83/adw-gtk3) to make GTK 3 apps consistent with GTK 4/ Libadwaita apps:

```bash
 sudo dnf install adw-gtk3-theme
```


!!! tip "How to:"
    open  GNOME Tweaks, then go to *Appearance*  --> *Styles*  --> *Legacy Applications* ,  and select **Adw-gtk3** or **Adw-gtk3-dark** from the menu.

### [Brave](https://brave.com/) Web Browser: Secure & Private by Design
!!! info "What is config-manager?"
    **config-manager** is a **DNF** plugin that simplifies adding, enabling, disabling, and removing repositories via command-line commands.
1.  Install the core plugins to enable the 'config-manager' command:
```bash
sudo dnf install dnf-plugins-core
```
 
 2.  Add the official Brave repository so that DNF can find the package:
```bash
sudo dnf config-manager addrepo --from-repofile=https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo
```

3.  Install Brave Browser:
```bash
sudo dnf install brave-browser
```

!!! question "Why add the Brave repository?"
    Installing via the official repository ensures your browser updates automatically alongside your system updates, keeping your browser secure and up-to-date.

### Install Codecs and Microsoft Fonts
Fedora includes only open-source licenses software in their official repositories, and it doesn’t ship with proprietary codecs (needed for MP 3 audio or MP 4/H.264 video playback) or Microsoft fonts by default. 

To fix that, we need add the **RPM Fusion** repositories first, then we could easily install the needed codecs and fonts:

1. **Add RPM Fusion Repositories:**
```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

2. **Enable Cisco OpenH264:** 
Fedora uses the OpenH264 library by default for web video (like WebRTC), but the repository needs to be explicitly enabled.
??? info "Why do I need to enable this explicitly?"
    H.264 video decoding is patented and requires royalty payments. Fedora, being 100% open-source, cannot distribute it or pay these fees.
    
    **The Solution:** Cisco has generously agreed to pay the licensing fees for everyone, but there is a legal catch: **You must download the binary directly from Cisco, not from Fedora.**
    
    By running the command above, you are simply telling `dnf` to fetch this files from Cisco's servers, keeping Fedora legally safe and your videos playing smoothly.

```bash
sudo dnf config-manager setopt fedora-cisco-openh264.enabled=1
```   
3. **Enable GUI Support (AppStream):**
By default, enabling RPM Fusion makes packages available in the terminal (`dnf`). To make them appear in graphical stores like **GNOME Software** or **KDE Discover** (with icons, screenshots, and descriptions), you need to install the AppStream metadata.

```bash
sudo dnf install rpmfusion-*-appstream-data
```
4.  **Installing the codecs:**


-  *Upgrade to Full FFmpeg*

Fedora ships with a limited version called `ffmpeg-free`. While it works for basic tasks, it often causes version mismatches and lacks support for many common formats.
For a stable experience, it is highly recommended to **swap** it with the full version provided by RPM Fusion.
```bash
sudo dnf swap ffmpeg-free ffmpeg --allowerasing
```

-  *Install Additional GStreamer Codecs*
 
 While FFmpeg handles the backend, many GUI applications (like the default **Videos** app or **Totem**) rely on the GStreamer framework. To ensure they can play all restricted formats:
```bash
sudo dnf update @multimedia --setopt="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
```

- *Enable Hardware Acceleration for Intel integrated GPUs:*
```bash
sudo dnf install intel-media-driver
```

- *Install Microsoft fonts:*
```bash
sudo dnf install curl cabextract xorg-x11-font-utils fontconfig; sudo rpm -ivh --nodigest --nofiledigest https://downloads.sourceforge.net/project/mscorefonts2/rpms/msttcore-fonts-installer-2.6-1.noarch.rpm 
```
### [Obsidian](https://obsidian.md/): The Best Note taking App
1. Ensure **Flathub** repository is enabled:

```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
2.  Install Obsidian
```bash
flatpak install flathub md.obsidian.Obsidian
```

### [Geary](https://gitlab.gnome.org/GNOME/geary): Lightweight GNOME Email Client
```bash
sudo dnf install geary
```

### [Gnome Extension Manager](https://mattjakeman.com/apps/extension-manager): The Best Way to Browse, Install and Manage GNOME Shell Extensions
```bash
flatpak install com.mattjakeman.ExtensionManager

```

List of extensions I use:


-  **[AppIndicator and KStatusNotifierItem Support](https://github.com/ubuntu/gnome-shell-extension-appindicator):** Adds  system tray icons support to the top panel.
- **[GSConnect](https://github.com/GSConnect/gnome-shell-extension-gsconnect/wiki):** To get notifications from my Android phone, share clipboard between my phone and my computer, and remote control my PC from my phone.
-  **[Clipboard Manager](https://github.com/Tudmotu/gnome-shell-extension-clipboard-indicator):** Like its name says, a clipboard manager for GNOME (saves text you copy so you don't lose it).
- **[Gtk4 Desktop Icons NG (DING)](https://gitlab.com/smedius/desktop-icons-ng):** Allows me adding my files and apps to the desktop. 
- **[Tiling Assistant](https://github.com/Leleat/Tiling-Assistant):** Brings Windows 11 style Snap Assistant to GNOME.
- **[Fedora Linux Update Indicator](https://github.com/purejava/fedora-update):** To get a  notification when new system updates are available.

### Install Visual Studio Code
1.  import The Microsoft GPG key:
```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```

2. Add the VS Code repository:
```bash
echo -e "[code]\nname=Visual Studio Code\nbaseurl=https://packages.microsoft.com/yumrepos/vscode\nenabled=1\nautorefresh=1\ntype=rpm-md\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" | sudo tee /etc/yum.repos.d/vscode.repo > /dev/null

```
3. Install the VS Code package:
```bash
sudo dnf install code --refresh
```


`#!python print("x")`