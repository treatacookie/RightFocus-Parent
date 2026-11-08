# Security Policy & Architecture — RightFocus Parent

**Last Updated:** November 7, 2026

RightFocus takes security and family privacy seriously. This document outlines the security architecture of **RightFocus Parent**, **RightFocus Child Agent**, and the **Cloudflare Worker Relay**, as well as instructions for reporting security vulnerabilities.

---

## 1. Security Architecture Overview

### 1.1 Zero Open Local Network Ports
- Unlike traditional localhost-server time trackers, `RightFocus-Parent.exe` and `RightFocus-Child.exe` **do not open any local TCP/HTTP listening ports**.
- All communication between the React 19 UI and the Rust backend in `RightFocus-Parent.exe` happens over in-process Tauri v2 IPC (`window.__TAURI_INTERNALS__`). Other processes or browser tabs on the machine cannot query your local database over `localhost`.

### 1.2 End-to-End Encrypted (E2EE) Child Sync (`AES-256-GCM`)
- When a parent creates a Child Profile in `RightFocus Parent`, the application generates three independent secrets using a cryptographically secure random number generator (`rand::rngs::OsRng` / WebCrypto):
  1. **`deviceToken`:** Used by `RightFocus-Child.exe` to authenticate `POST /api/v1/push` requests to the Relay Worker.
  2. **`syncKey` (256-bit / 32 bytes):** Used exclusively on the Child PC and Parent PC for authenticated encryption. **The `syncKey` is never sent to the Cloudflare Relay Worker.**
  3. **`parentApiKey`:** Used by `RightFocus-Parent.exe` to authenticate `/api/v1/pull`, `/api/v1/ack`, and `/api/v1/register-device` requests.
- Before uploading activity events, `RightFocus-Child.exe` serializes the batch to JSON, compresses it with `gzip` (`flate2`), generates a fresh 96-bit random nonce (`IV`), and encrypts the payload using **AES-256-GCM** (`aes-gcm` crate) with an authenticated 128-bit GCM tag.
- On the Parent PC, `RightFocus-Parent.exe` verifies the AES-256-GCM authentication tag before decompressing and inserting events into SQLite. Tampered or corrupted batches are rejected automatically.

### 1.3 Zero-Plaintext Token Storage on the Relay
- The Cloudflare Relay Worker stores only the **SHA-256 hash** of the `parentApiKey` and each child's `deviceToken` inside the D1 database (`relay_config` and `devices` tables).
- Token hashes are verified using constant-time byte comparison to prevent timing side-channel attacks.
- Push payloads are size-capped at the Worker boundary to prevent storage exhaustion.

### 1.4 Cryptographically Verified Background Updates (`SHA-512`)
- Every release publishes `latest-parent.yml` and `latest-child.yml` manifests containing the exact `sha512` digest of the NSIS installer (`RightFocus-Parent-Setup-<ver>.exe` and `RightFocus-Child-Setup-<ver>.exe`).
- Both the Parent and Child background updaters compute the SHA-512 hash of the downloaded installer and verify an exact match before executing the installer. If verification fails, the downloaded file is immediately deleted and never executed.

---

## 2. Supported Versions

Security updates are distributed automatically via the built-in background updater and published to the latest release on GitHub:

| Version | Supported |
| :--- | :--- |
| **`0.7.x` (Latest Release)** | ✅ Supported |
| **`< 0.7.0`** | ❌ Please upgrade to the latest release |

---

## 3. Reporting a Vulnerability

If you discover a security vulnerability in RightFocus Parent, RightFocus Child Agent, or the Cloudflare Relay Worker:

1. **Please do NOT open a public GitHub issue containing exploit details** before a fix has been released.
2. Instead, please report the issue via [GitHub Security Advisories](https://github.com/treatacookie/RightFocus-Parent/security/advisories/new) or open a minimal contact issue on [https://github.com/treatacookie/RightFocus-Parent/issues](https://github.com/treatacookie/RightFocus-Parent/issues) requesting a private communication channel.
3. Include affected versions, reproduction steps, and potential impact. We aim to acknowledge reports within 72 hours and publish a patched release promptly.

