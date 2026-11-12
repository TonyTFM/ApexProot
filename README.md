ApexLinux Proot-Distro

# 🏴‍☠️ 1.0 ApexLinux PRoot Edition

Willkommen im Hauptquartier von **LinxOS** (`GN9@ApexLinux`). Dieses Projekt kombiniert eine automatisierte Termux-Umgebung mit einem vollwertigen, isolierten **ARM64 PRoot-Container** auf Ubuntu-Basis — entwickelt für maximale Kontrolle, portables Arbeiten und echte Linux-Power direkt auf dem Smartphone.

---

## 🚀 Features

* **ApexLinux PRoot-Container (`ARM64`):** Cross-kompiliertes Ubuntu-Rootfs (`debootstrap --foreign`), optimiert für `proot-distro` in Termux.
* **Godmode-Terminal (`GN9`):** Vorkonfigurierte Shell-Umgebung mit persönlichen Aliasen, Custom-Prompt und direkten System-Skripten.
* **One-Click Deployment (`install-git_termux.sh`):** Automatisiertes Setup-Skript für frische Termux-Installationen inklusive Update-Logik.

---

## ⚡ Quickstart: Termux-Basis installieren

Führe diesen Einzeiler in einer frischen Termux-Umgebung aus, um das Repository zu klonen und die Basis-Skripte zu aktivieren:

```bash
pkg update -y && pkg install -y git curl && git clone [https://github.com/TonyTFM/LinxOS.git](https://github.com/TonyTFM/LinxOS.git) ~/LinxOS && cd ~/LinxOS && chmod +x install-git_termux.sh && ./install-git_termux.sh

📦 ApexLinux PRoot-Container einrichten

Um das vollwertige ApexLinux (GN9) Root-System in Termux zu nutzen:
1. Voraussetzungen installieren
Bash

pkg update && pkg install proot-distro -y

2. Distro-Plugin hinterlegen

Kopiere das Archiv apex-proot-arm64.tar.xz nach /sdcard/Download/ und erstelle das Plugin unter $PREFIX/etc/proot-distro/apex.sh:
Bash

cat << 'EOF' > $PREFIX/etc/proot-distro/apex.sh
DISTRO_NAME="ApexLinux (GN9)"
TARBALL_URL['aarch64']="file:///sdcard/Download/apex-proot-arm64.tar.xz"
TARBALL_SHA256['aarch64']="<HIER_SHA256_HASH_EINTRAGEN>"
EOF

(Den SHA256-Hash erzeugst du auf deinem Linux-PC mit sha256sum apex-proot-arm64.tar.xz)
3. Container installieren & Second-Stage abschließen
Bash

proot-distro install apex
proot-distro login apex -- /debootstrap/debootstrap --second-stage

4. System booten
Bash

proot-distro login apex

🛠️ Eigenes ARM64-Image bauen (Linux x86_64 Host)

Falls du das Root-Dateisystem auf deinem Linux-PC (z. B. Zorin OS / Linux Mint) selbst neu bauen möchtest:
Bash

sudo apt update && sudo apt install -y debootstrap proot tar
mkdir -p ~/ApexProot/apex-rootfs && cd ~/ApexProot
sudo debootstrap --arch=arm64 --foreign noble ~/ApexProot/apex-rootfs [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
sudo cp ~/.bashrc ~/ApexProot/apex-rootfs/root/.bashrc
sudo tar -cJf apex-proot-arm64.tar.xz -C ~/ApexProot/apex-rootfs .

👤 Autor

    TonyTFM / GN9 — GitHub Profil


