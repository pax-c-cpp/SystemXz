<div align="center">
  <img src="https://github.com/user-attachments/assets/422c3db0-272d-4a7b-a734-2375467ee661" alt="SysXz Logo" width="200"/>
  <h1>SysXz (System XZ)</h1>
  <p><strong>A Linux Distribution Built for Control and Transparency.</strong></p>

  <p>
    <img src="https://img.shields.io/badge/Version-1.1_(DEVTest)-informational?style=flat-square" alt="Version">
    <img src="https://img.shields.io/badge/Base-Debian_12-critical?style=flat-square&logo=debian" alt="Base">
    <img src="https://img.shields.io/badge/Init-OpenRC-success?style=flat-square" alt="Init">
    <img src="https://img.shields.io/badge/Desktop-Openbox-orange?style=flat-square" alt="Desktop">
    <img src="https://img.shields.io/badge/License-GSPL_1.1-blueviolet?style=flat-square" alt="License">
  </p>
</div>

---

## Foreword

SystemXz was born out of a specific engineering requirement: to create a desktop operating system that respects the user's hardware resources, adheres to traditional Unix philosophies, and remains fully transparent from the bootloader to the window manager. 

Unlike mainstream distributions that abstract away system internals through heavy init systems and monolithic desktop environments, SystemXz takes a deliberate step backward to move forward. It is designed for developers, system administrators, and power users who require absolute control over their environment.

---

## Technical Specifications (System Matrix)

To ensure full transparency, the following table details the exact core components and versions utilized in the SystemXz 1.1 (DEVTest) build.

| Component | Software / Implementation | Version (Target) | Rationale |
| :--- | :--- | :--- | :--- |
| **Kernel** | Linux (Debian LTS) | `6.1.x` | Long-Term Support for maximum hardware compatibility and security patches. |
| **C Library** | glibc | `2.36` | Standard Debian library; ensures binary compatibility with the vast Debian ecosystem. |
| **Init System** | OpenRC | `0.45.x` | Replaces systemd for transparent, script-based service management. |
| **Service Manager** | OpenRC (rc-update) | `0.45.x` | Native dependency handling without D-Bus or binary logs. |
| **Display Server** | Xorg (X11) | `21.1.x` | Mature, stable, and universally supported display protocol. |
| **Display Manager** | XDM | `1.1.13` | Minimalist graphical login; zero unnecessary dependencies. |
| **Window Manager** | Openbox | `3.6.x` | Highly configurable, lightweight, and EWMH compliant. |
| **Shell (/bin/sh)** | Dash | `0.5.12` | Strict POSIX compliance and faster execution than Bash. |
| **Terminal Emulator** | Xterm | `379` | The standard, no-nonsense terminal for X11. |
| **Taskbar / Panel** | Tint2 | `17.0` | Lightweight, highly customizable taskbar for Openbox. |
| **Wallpaper Setter** | Feh | `3.9` | Fast and scriptable image viewer/wallpaper setter. |
| **Bootloader** | GRUB 2 | `2.06` | Universal support for both Legacy BIOS and UEFI systems. |
| **Build System** | `live-build` | `3.0` | Debian's official tool for generating hybrid ISOs. |

---

## Architectural Decisions

The architecture of SystemXz is the result of pragmatic engineering choices, not ideological dogma.

*   **Debian Core (glibc):** We chose Debian 12 as our base package repository and toolchain. This decision guarantees access to the most stable and extensive software repositories available in the Linux ecosystem.
*   **OpenRC as PID 1:** We consciously removed `systemd`. OpenRC provides a transparent, script-based service management layer. It boots faster, utilizes fewer resources, and allows administrators to audit and modify service behavior without wrestling with binary logs.
*   **Dash over Bash:** The default `/bin/sh` is linked to `dash`. This enforces strict POSIX compliance for system scripts and reduces the memory footprint during early boot stages.
*   **Lean Graphical Stack:** Openbox and Xorg are intentionally chosen to provide a mature, responsive desktop without the overhead of a full desktop environment.

---

## The "Z Philosophy"

The development of SystemXz is guided by an internal engineering framework known as the Z Philosophy:

1.  **Efficiency:** No background daemons or services are included unless they serve a direct, immediate user purpose.
2.  **Transparency:** Every script, configuration file, and init service is human-readable and modifiable.
3.  **Simplicity:** We avoid abstraction layers that do not provide tangible benefits to the end-user experience.
4.  **Control:** The system assumes the user knows what they are doing and provides the tools to do it.

---

## Installation & Deployment

SystemXz includes a custom, interactive TUI (Text User Interface) installer written in C. It was developed to provide a lightweight, dependency-free installation process that handles disk partitioning, filesystem formatting, and bootloader deployment without the overhead of a graphical installer.

To build the SystemXz ISO from source, the build environment requires `live-build` and `xorriso`.

```bash
# Clone the repository
git clone https://github.com/yourusername/SystemXz.git
cd SystemXz/systemxz-live

# Initiate the ISO build process (requires root privileges)
sudo lb build
