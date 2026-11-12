# 🏴‍☠️ (v1.0 ApexLinux PRoot Edition)

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
