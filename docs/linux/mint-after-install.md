---
icon: simple/linuxmint
---

# Things I Do After Installing Linux Mint

Linux Mint is a popular and user-friendly distribution of the Linux operating system, known for its simplicity, stability, and extensive hardware support.

Although Linux Mint is designed to be ready-to-use out of the box, there are several steps that I take to customize the OS to my liking and optimize it for my specific day-to-day needs:
## Updating The System:

As with every operating system installation, the first step I do is update the system to ensure I have the latest security patches and software updates:
```bash
sudo apt update && sudo apt full -upgrade -y
```

## Installing Brave: 

Brave is my browser of choice,because it's built on the Chromium engine, ensuring compatibility with a wide range of web applications and extensions, while also providing enhanced privacy features such as built-in ad blocking and tracking protection:

1- First, We need to add the Brave repository to ensure we receive the latest browser updates with the rest of our system updates. To do this, we open the terminal and execute the following commands:
```bash
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
```

```bash
sudo curl -fsSLo /etc/apt/sources.list.d/brave-browser-release.sources https://brave-browser-apt-release.s3.brave.com/brave-browser.sources
```

2- After adding the Brave repository, we need to update the package list to include the Brave browser packages. This is done by running the following command in the terminal:
```bash
sudo apt update
```

3- Finally, we can install Brave by executing the following command:
```bash
sudo apt install brave-browser -y
```

## Installing Obsidian: The best Note Taking App:

The easiest way to install Obsidian on Linux Mint is using flatpak, as it comes pre-installed and even with the Flathub repository configured. In the terminal, just type the following command to install Obsidian:

```bash
flatpak install flathub md.obsidian.Obsidian
```

## Installing OnlyOffice:
Unlike LibreOffice included with Linux Mint, which converts  Microsoft Office files (docx, xlsx, and pptx) first into its own format -- called OpenDocument Format (ODF) --  before it can open or save them, which often causes these files to be displayed differently from Microsoft Office,  OnlyOffice was built from the beginning on the OOXML  format , the same architecture and format used by  Microsoft in its Office programs Word, Excel, and PowerPoint. Therefore, it is intuitive and natural that Office files appear in their format, lines and tables when opened by OnlyOffice. 

OnlyOffice also comes with a better, prettier, and more familiar modern interface that’s more similar to that on Microsoft Office programs than the classic one in Libre Office, making OnlyOffice my favorite option to handle and share Office files with friends and at home.

To install it on Linux Mint, we will first add  OnlyOffice repository as always following these  steps:
```bash
mkdir -p -m 700 ~/.gnupg && gpg --no-default-keyring --keyring gnupg-ring:/tmp/onlyoffice.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys CB2DE8E5 && chmod 644 /tmp/onlyoffice.gpg && sudo chown root:root /tmp/onlyoffice.gpg && sudo mv /tmp/onlyoffice.gpg /usr/share/keyrings/onlyoffice.gpg
```

```bash
echo 'deb [signed-by=/usr/share/keyrings/onlyoffice.gpg] https://download.onlyoffice.com/repo/debian squeeze main' | sudo tee -a /etc/apt/sources.list.d/onlyoffice.list
```

!!!note "Note from the OnlyOffice Website:"
	While the APT package is built against Debian Squeeze, it is compatible with a number of Debian derivatives (including Ubuntu), which means you can use the same repository across all these distributions.

After that, use the following command to install OnlyOffice:

```bash
sudo apt update && sudo apt install onlyoffice-desktopeditors -y
```

## Install build-essential:
build-essential is a software package that includes essential tools for building and compiling software in Linux. It provides a set of basic development tools such as compilers (gcc, g++), the make utility, and other necessary libraries.
```bash
sudo apt install build-essential
```

## Install  git, a version control system:
git is the version control  system  I use for tracking changes in source code during software development.  unfortunately does not come pre-installed with Linux Mint (just like Ubuntu), but it  is can be installed easily using this command:
```bash
sudo apt install git
```
