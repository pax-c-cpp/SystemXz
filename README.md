<div align="center">
  <img src="https://github.com/user-attachments/assets/422c3db0-272d-4a7b-a734-2375467ee661" alt="SysXz Logo" width="200"/>
  <h1>SysXz (System XZ)</h1>
  <p><strong>A lightweight, secure, and rational Linux-based operating system built from scratch.</strong></p>
  <p>
    <img src="https://img.shields.io/badge/Built_with-Buildroot-blue?style=flat-square" alt="Buildroot">
    <img src="https://img.shields.io/badge/Init-OpenRC-green?style=flat-square" alt="OpenRC">
    <img src="https://img.shields.io/badge/Libc-musl-orange?style=flat-square" alt="musl">
    <img src="https://img.shields.io/badge/Pkg_Manager-APK-red?style=flat-square" alt="APK">
    <img src="https://img.shields.io/badge/Philosophy-Z-purple?style=flat-square" alt="Z Philosophy">
  </p>
</div>

---

## What is SysXz?

**SysXz** (pronounced *System X-Zee*) is a custom, general-purpose Linux distribution designed for daily use and software development. It is built completely from source using **Buildroot**, ensuring that every component is optimized, secure, and serves a clear purpose.

Unlike bloated distributions, SysXz is not just another Linux distro; it is a **statement of engineering**. It strictly adheres to the **Z Philosophy**—a set of principles focused on efficiency, security, simplicity, and rational choice.

### Key Features
*   **Ultra-Lightweight:** No unnecessary daemons or background services.
*   **Built from Scratch:** Powered by Buildroot for maximum control.
*   **OpenRC Init System:** Fast, transparent, and script-based initialization (No systemd).
*   **musl libc:** A clean, fast, and secure C standard library.
*   **APK Package Manager:** Alpine's blazing-fast package manager, integrated natively.
*   **Xorg + Openbox:** A minimalist, highly customizable graphical environment.
*   **Custom Identity:** Features a unique boot logo and Z-philosophy branding.

---

## The Z Philosophy

SysXz is governed by the **Z Philosophy** and **IDIORC** (*I Don't Care If It's Open or Closed*). We don't worship tools; we choose the best tool for the job based on rationality.

1.  **Efficiency:** Optimal use of CPU, RAM, and storage.
2.  **Security:** Security is designed-in, not bolted-on.
3.  **Privacy:** Zero telemetry. Zero tracking. Your data is yours.
4.  **Simplicity:** Every component must justify its existence.
5.  **Modifiability:** Easy to understand, patch, and extend.
6.  **Freedom (IDIORC):** Quality and suitability over licensing dogmas.

---

## Technical Stack (The Details)

SysXz is assembled using the following core technologies. This table represents the exact stack used to build the system:

| Component | Technology | Why we chose it |
| :--- | :--- | :--- |
| **Build System** | [Buildroot](https://buildroot.org/) | Absolute control over the build process. |
| **Kernel** | Linux 6.1 LTS | Modern hardware support with long-term stability. |
| **Init System** | [OpenRC](https://github.com/OpenRC/openrc) | Lightweight, transparent, and avoids systemd complexity. |
| **C Library** | [musl](https://musl.libc.org/) | Fast, secure, and standards-compliant. |
| **Package Manager** | [APK](https://gitlab.alpinelinux.org/alpine/apk-tools) | Extremely fast, built-in dependency resolution. |
| **Graphical Server** | [Xorg](https://www.x.org/) | Proven stability, universal compatibility. |
| **Window Manager** | [Openbox](http://openbox.org/) | Minimal, fast, and highly configurable. |
| **Display Manager** | [XDM](https://www.x.org/archive/X11R7.5/doc/man/man1/xdm.1.html) | Simple GUI login, no heavy dependencies. |
| **Graphics** | [Mesa3D](https://mesa3d.org/) | OpenGL support (GLX) for applications. |
| **Shell** | Dash | POSIX-compliant, blazing fast `/bin/sh`. |
| **Toolchain** | GCC (Host) | Compiling the target system. |

---

## Building SysXz from Source

To build SysXz yourself, follow these steps:

### Prerequisites
You need a Linux host (we used openSUSE) with the following tools installed:
```bash
sudo zypper install gcc gcc-c++ make bc git patch libncurses-devel \
  wget cpio rsync unzip file tar bzip2 xz zstd findutils \
  perl python3 gawk bison flex gettext libtool
```

### warn!!:
there is a bug on Musl and Musl-based SSHD
that can harm the user , be aware please.
