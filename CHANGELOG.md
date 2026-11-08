# Changelog

All notable public release changes to **RightFocus Parent** & **RightFocus Child Agent** are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [0.7.8] - 2026-11-08

### Initial Public Release
- **RightFocus Parent (`RightFocus-Parent-Setup-0.7.8.exe`):**
  - Local-first Windows desktop activity and screen-time dashboard built with Rust, Tauri v2, and React 19.
  - Per-device profile switching between **This PC (Parent)** and any number of **Child** profiles across Dashboard, Timeline, Calendar, Top Apps, Categories, Raw Events, and Data management.
  - Smart **Categories** rule builder with 16 starter categories, 280+ curated Windows applications, app-first auto-correlation, and 1-click **Suggested Uncategorized Apps**.
  - 1-click automated Cloudflare Worker + D1 end-to-end encrypted relay provisioning in `Settings → Multi-Device Cloud Relay`.
- **RightFocus Child Agent (`RightFocus-Child-Setup-0.7.8.exe`):**
  - Ultra-lightweight native Win32 background agent (~4 MB RAM, zero WebView/Chromium runtime) with offline SQLite store-and-forward buffering, client-side AES-256-GCM encryption, and silent background auto-updates.
