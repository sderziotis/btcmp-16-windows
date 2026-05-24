# BTCMP-16 — Digital Forensics Lab Environment

## Overview

This lab environment is built around a **Digital Forensics** scenario. It uses **windows-10-x86_64** for the analyst workstation and **windows-server-2019-x86_64** for the victim/evidence machine. Both machines share the same internal network, routed through `router-1`.

---

## Topology

| Host | Role | Network | CIDR | IP |
|------|------|---------|------|----|
| wavm | Analyst Workstation (Win 11) | network-2 | 192.168.10.0/24 | 192.168.10.10 |
| wvvm | Victim/Evidence Machine (WS 2025) | network-2 | 192.168.10.0/24 | 192.168.10.20 |

---

## Machines

### WAVM — Analyst Workstation (Windows 10)
User `user` / `Password123` (admin enabled).

**Software:**
- Git
- FTK Imager 4.7.1.2
- Autopsy / Sleuth Kit (TSK) 4.21.0
- RegRipper 4.0 (cloned to `C:\Tools\RegRipper4.0`)
- Registry Explorer by Eric Zimmermann (extracted to `C:\Tools\RegistryExplorer`)

**Notes:**
- Git, FTK Imager, Autopsy, and Strawberry Perl are all installed via **Chocolatey** — no hardcoded download URLs, so these will not go stale.
- RegRipper 4.0 is cloned from https://github.com/keydet89/RegRipper4.0. It runs via `perl rip.pl` — Strawberry Perl is installed to satisfy this dependency.
- Registry Explorer is downloaded from the **official EZ Tools GitHub releases** (`/latest/download/` redirect) — this always resolves to the newest release automatically. If it ever goes stale, check https://ericzimmerman.github.io.
- All tools without an installer are extracted/cloned to `C:\Tools\`.

---

### WVVM — Victim / Evidence Machine (Windows Server 2019)
User `user` / `Password123` (admin enabled).

**Software:** None — bare Windows Server 2019 installation.

---

## Notes
- The `community.windows` Ansible collection is required for the `win_unzip` module used to extract Registry Explorer.
