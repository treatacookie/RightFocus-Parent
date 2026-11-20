# Privacy Policy — RightFocus Parent & Child Agent

**Last Updated:** November 7, 2026

**RightFocus** (`RightFocus-Parent` and `RightFocus-Child`) is designed from the ground up with a **100% local-first, zero-knowledge privacy architecture**.

The creators and maintainers of RightFocus (**TreatACookie / RightFocus**) **do not operate any central servers, do not require user accounts, and never collect, receive, store, or have access to your or your family's activity data, telemetry, or encryption keys.**

---

## 1. Information Recorded Locally on Your Devices

When running on a computer, RightFocus records screen-time and application activity locally on that device:

1. **Foreground Application Activity:**
   - The executable name of the active foreground window (e.g., `chrome.exe`, `Code.exe`, `Minecraft.exe`).
   - The active window title (unless disabled via the **"Don't record window titles"** setting in `Settings`).
   - Timestamps and duration of each activity span.
2. **Idle / AFK (Away From Keyboard) Status:**
   - Seconds since the last mouse or keyboard input (via the standard Windows `GetLastInputInfo` API) to determine whether the user is actively at the computer (`not-afk`) or away (`afk`).
   - **RightFocus never logs keystrokes, mouse coordinates, screenshots, webcam feeds, microphone audio, or clipboard contents.**
3. **Device Metadata:**
   - The local computer's hostname and operating system platform identifier.

### Where Data is Stored Locally
- **On the Parent PC (`RightFocus-Parent.exe`):** All local and synced child activity is stored in a local SQLite database at `%APPDATA%\rightfocus-parent\rightfocus.db`.
- **On a Child PC (`RightFocus-Child.exe`):** Pending activity batches are buffered temporarily in `%APPDATA%\rightfocus-child\child-buffer.db` and purged automatically once encrypted and delivered to the Parent PC.

---

## 2. Built-In Privacy Controls

RightFocus gives you complete control over what is recorded and stored:

- **Title Redaction (`Don't record window titles`):** You can disable window title recording at any time in `Settings → Tracking (This PC)` so that only application executable names are logged.
- **Excluded Applications (`Exclude apps`):** You can specify executables (such as password managers like `1Password.exe`, `Bitwarden.exe`, `KeePass.exe`) that RightFocus will never record.
- **Full Data Ownership, Export & Wipe:** From the `Data` page, you can inspect the exact SQLite file path on disk, export all data to JSON or CSV, or permanently wipe any time range or the entire database.

---

## 3. Multi-Device Cloud Relay & End-to-End Encryption (E2EE)

If you use RightFocus solely on a single PC, **zero network traffic** is ever generated for activity tracking.

If you optionally enable **Multi-Device Cloud Relay** to monitor a child's PC remotely:

1. **User-Owned Infrastructure:**
   - The Cloud Relay runs inside **your own personal Cloudflare account** (using Cloudflare Workers and Cloudflare D1 on Cloudflare's free tier), either deployed via the built-in 1-Click Cloudflare provisioner or connected manually.
   - RightFocus creators have zero access to your Cloudflare account, Worker, or D1 database.
2. **Client-Side End-to-End Encryption (AES-256-GCM):**
   - When you create a Child Profile on the Parent PC, a random 256-bit symmetric encryption key (`syncKey`) is generated locally and embedded in the `RFP-...` Pairing Code.
   - Before any activity batch leaves the Child PC, `RightFocus-Child.exe` compresses the payload (`gzip`) and encrypts it locally using **AES-256-GCM** with a random 96-bit initialization vector (`IV`).
   - The Cloudflare Relay Worker stores only the opaque encrypted ciphertext (`ciphertext` + `iv`). Neither Cloudflare nor any third party can read the application names or window titles inside the encrypted payload.
3. **Ephemeral Relay Buffering:**
   - Once the Parent PC downloads, decrypts, and verifies an encrypted batch into its local SQLite database, it sends an acknowledgment (`POST /api/v1/ack`) that immediately deletes those encrypted rows from the Cloudflare D1 database.

---

## 4. Children's Privacy (COPPA & GDPR-K Notice)

RightFocus Parent is a tool designed for parents and legal guardians to manage and understand screen-time habits on computers used by their children:

- Because **zero data is ever transmitted to or collected by the creators of RightFocus**, RightFocus does not collect personal information from children under the U.S. Children's Online Privacy Protection Act (COPPA) or the EU General Data Protection Regulation (GDPR).
- All data recorded by `RightFocus-Child.exe` remains strictly under the custody and control of the parent or legal guardian who paired the device.

---

## 5. External Network Requests

RightFocus makes external network connections **only** in the following circumstances:

1. **Background Update Checks (`GitHub Releases`):**
   - `RightFocus-Parent.exe` and `RightFocus-Child.exe` periodically query the public GitHub Releases API (`https://github.com/treatacookie/RightFocus-Parent`) to check for new versions (`latest-parent.yml` / `latest-child.yml`) and download signed SHA-512 verified installer updates. Standard HTTP request headers (IP address, User-Agent) are processed by GitHub in accordance with [GitHub's Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement).
2. **Optional Cloudflare Relay Provisioning & Sync:**
   - When you configure or use the Multi-Device Cloud Relay, the app communicates directly with the Cloudflare API (`api.cloudflare.com`) and your personal Cloudflare Worker URL (`*.workers.dev`).

---

## 6. Contact & Questions

If you have questions about this Privacy Policy or RightFocus's privacy architecture, please open an issue on our public repository:
- **GitHub Issues:** [https://github.com/treatacookie/RightFocus-Parent/issues](https://github.com/treatacookie/RightFocus-Parent/issues)

