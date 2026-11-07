# RightFocus Parent

**Local-First Screen-Time Analytics & End-to-End Encrypted Multi-Device Parental Monitoring for Windows.**

[![Latest Release](https://img.shields.io/github/v/release/treatacookie/RightFocus-Parent?label=Latest%20Release&color=2b7fff)](https://github.com/treatacookie/RightFocus-Parent/releases/latest)
[![Platform: Windows 10/11](https://img.shields.io/badge/Platform-Windows%2010%20%2F%2011%20(x64)-0078D6)](https://github.com/treatacookie/RightFocus-Parent/releases/latest)
[![License: MIT](https://img.shields.io/badge/License-MIT-22c55e)](LICENSE)

---

## Overview

**RightFocus Parent** is a lightweight, high-precision desktop activity tracker and parental screen-time dashboard built with **Rust**, **Tauri v2**, and **React 19**.

Inspired by [ActivityWatch](https://activitywatch.net/) for core local activity tracking, **RightFocus Parent** extends local time tracking with **End-to-End Encrypted (AES-256-GCM) multi-device child synchronization** over your own free Cloudflare account — giving parents complete visibility into their children's screen time across multiple PCs with **zero subscription fees** and **zero third-party data collection**.

---

## Key Features

- **Ultra-Lightweight Native Binaries:**
  - **`RightFocus-Parent-Setup.exe` (~2.6 MB):** Full analytics dashboard for the Parent PC with system tray support and automatic local SQLite storage (`%APPDATA%\rightfocus-parent\rightfocus.db`).
  - **`RightFocus-Child-Setup.exe` (~1.3 MB):** Pure native Win32 background agent for Child PCs (~4 MB RAM, zero WebView/Chromium overhead, single background process).
- **Rich Screen-Time Insights (Per-Device Profile Switching):**
  - Switch effortlessly between **`🖥 This PC (Parent)`** and any number of **`💻 <Child Name>`** profiles from the top-left `Active Profile` selector.
  - **Dashboard:** Daily, weekly, monthly, and yearly active time summaries, category breakdowns, and top apps/window titles.
  - **Timeline:** Zoomable, interactive multi-day visual timeline of active (`not-afk`), idle (`afk`), and application usage spans.
  - **Calendar:** Day, Week, and Month activity block views.
  - **Top Apps & Categories:** Custom date ranges, regex-based category hierarchy with priority ordering, and historical retrospective recategorization.
  - **Raw Events & Data Management:** Full JSON/CSV export, backup import, and selective time-range or full database wipe.
- **1-Click Zero-Knowledge Cloud Relay (Cloudflare Workers + D1):**
  - Connect your own free Cloudflare account in `Settings → Multi-Device Cloud Relay` to automatically provision an encrypted D1 relay in seconds.
  - All child activity batches are compressed (`gzip`) and encrypted client-side with **AES-256-GCM** before leaving the Child PC. Only your Parent PC holds the decryption key.
- **Offline Store-and-Forward Resilience:**
  - If a Child PC goes offline, `RightFocus-Child.exe` buffers activity spans locally in SQLite and automatically syncs them as soon as internet connectivity returns.

---

## Downloads & Installation

Download the latest installers from [**GitHub Releases**](https://github.com/treatacookie/RightFocus-Parent/releases/latest):

| Installer | Target PC | Size | Description |
| :--- | :--- | :--- | :--- |
| **`RightFocus-Parent-Setup-<ver>.exe`** | Parent's PC | ~2.6 MB | Full Parent dashboard + local activity tracker |
| **`RightFocus-Child-Setup-<ver>.exe`** | Child's PC | ~1.3 MB | Lightweight background agent paired via `RFP-...` code |

### Quick Start: Pairing a Child's PC

1. **Install RightFocus Parent** on your PC and open `Settings → Multi-Device Cloud Relay`.
2. Click **1-Click Connect with Cloudflare (Free)** to automatically deploy your private Relay Worker and D1 database.
3. Open the **Child Devices** tab in the sidebar, enter your child's device name (e.g., `Alex Laptop`), and click **Generate Pairing Code** to copy the `RFP-...` code.
4. On the child's Windows PC, run **`RightFocus-Child-Setup-<ver>.exe`**, paste the `RFP-...` Pairing Code into the one-time setup window, and click **Connect & Run in Background**.
5. Select your child's profile from the top-left **Active Profile** dropdown on your Parent PC to view their synced activity.

---

## Managing or Uninstalling the Child Agent

- **Re-open Pairing Setup Dialog on Child PC:**
  ```powershell
  "%LOCALAPPDATA%\Programs\rightfocus-child\RightFocus-Child.exe" --setup
  ```
- **Uninstall Child Agent from Child PC:**
  ```powershell
  "%LOCALAPPDATA%\Programs\rightfocus-child\Uninstall-RightFocus-Child.exe"
  ```
- **Diagnostic Log Location on Child PC:**
  - `%APPDATA%\rightfocus-child\child-agent.log` (256 KB self-trimming ring buffer).

---

## Legal, Privacy & Security Documentation

> **Authorized Use Notice:** RightFocus Child Agent is intended strictly for parents or legal guardians managing devices used by their minor children, or for device owners with the explicit consent of the user. Unauthorized installation on another adult's device without consent is strictly prohibited.

- [**License (`MIT`)**](LICENSE) — Open-source MIT License terms.
- [**Privacy Policy (`PRIVACY.md`)**](PRIVACY.md) — Local-first storage, E2EE Cloudflare sync architecture, and COPPA/GDPR-K compliance.
- [**Terms of Use (`TERMS.md`)**](TERMS.md) — Authorized Parental / Device-Owner Use mandate and warranty disclaimers.
- [**Security Policy (`SECURITY.md`)**](SECURITY.md) — AES-256-GCM encryption, SHA-256 token hashing, SHA-512 update verification, and vulnerability disclosure.
- [**Third-Party Notices (`THIRD_PARTY_NOTICES.md`)**](THIRD_PARTY_NOTICES.md) — Attributions for ActivityWatch inspiration, Tauri, React, SQLite, Rust crates, and Microsoft WebView2.
- [**Changelog (`CHANGELOG.md`)**](CHANGELOG.md) — Full version history and release notes.

