# Things I Do After Installing Fedora Workstation:


## Updating the system:

```bash
sudo dnf upgrade --refresh -y
```

## Installing some useful missing apps:

### GNOME Tweaks to add *maximize* and *minimize* buttons to the apps window:

```bash
 sudo dnf install gnome-tweaks
```

> [!TIP]  How to:
> open  Gnome Tweaks, then go to *Windows* --> *Titlebar Buttons*, and switch on **Maximize** and **Minimize**.

### [Adw-gtk3](https://github.com/lassekongo83/adw-gtk3) to make GTK 3 apps consistent with GTK 4/ Libadwaita apps:

```bash
 sudo dnf install adw-gtk3-theme
```


> [!TIP]  How to:
> open  GNOME Tweaks, then go to *Appearance*  --> *Styles*  --> *Legacy Applications* ,  and select **Adw-gtk3** or **Adw-gtk3-dark** from the menu.

### [Brave](https://brave.com/) Web Browser: Secure & Private by Design
1.  Install the core plugins to enable the 'config-manager' command:
```bash
sudo dnf install dnf-plugins-core
```

> [!INFO] What is config-manager?
> **config-manager** is a **DNF** plugin that simplifies adding, enabling, disabling, and removing repositories via command-line commands.

 2.  Add the official Brave repository so that DNF can find the package:
```bash
sudo dnf config-manager addrepo --from-repofile=https://brave-browser-rpm-release.s3.brave.com/brave-browser.repo
```

3.  Install Brave Browser:
```bash
sudo dnf install brave-browser
```


> [!QUESTION] Why add the Brave repository?
> Installing via the official repository ensures your browser updates automatically alongside your system updates, keeping your browser secure and up-to-date.

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
