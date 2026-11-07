# Terms of Use & Authorized Use Policy — RightFocus Parent

**Last Updated:** November 7, 2026

Please read these Terms of Use ("Terms") carefully before installing or using **RightFocus Parent** (`RightFocus-Parent.exe`) or the **RightFocus Child Agent** (`RightFocus-Child.exe`). By installing, pairing, or running the software, you agree to be bound by these Terms.

---

## 1. Authorized Parental & Device-Owner Use Mandate (Strictly Enforced)

**RightFocus Parent** and **RightFocus Child Agent** are designed exclusively for **personal productivity tracking** and **lawful parental screen-time management**.

By installing or pairing `RightFocus-Child.exe` on any computer, you explicitly represent, warrant, and agree that:

1. **Device Ownership or Legal Authority:** You are the lawful owner or authorized administrator of the computer on which the software is installed; **AND**
2. **Parental Guardianship or Explicit Consent:** You are either:
   - The **parent or legal guardian** of the minor child who uses the computer, acting within your lawful parental authority in your jurisdiction; **OR**
   - Installing the software on your own computer for personal use, or with the **explicit prior knowledge and consent** of the adult individual using the device.

### Strictly Prohibited Uses (Zero Tolerance for Unauthorized Monitoring)
- **You may NOT install, deploy, or use RightFocus to monitor any spouse, partner, roommate, colleague, employee, or other adult without their explicit knowledge and legal consent.**
- Installing monitoring software on a device you do not own or have legal authority to administer may violate federal, state, and international laws (including the U.S. Computer Fraud and Abuse Act, Electronic Communications Privacy Act, UK Computer Misuse Act, and EU privacy laws) and carries severe civil and criminal penalties.
- The authors and copyright holders of RightFocus assume **zero liability** for any misuse, unauthorized installation, or unlawful monitoring performed using this software.

---

## 2. Open-Source License

RightFocus is licensed under the **MIT License** (see [`LICENSE`](LICENSE)). Your right to use, copy, modify, and distribute the software is governed by the MIT License, subject to compliance with applicable laws as described in Section 1.

---

## 3. Uninstallation & Administrative Control

Parents and device administrators can inspect, reconfigure, or completely remove RightFocus at any time:

- **RightFocus Parent (`RightFocus-Parent.exe`):**
  - Can be uninstalled via **Windows Settings → Apps → Installed Apps → RightFocus Parent**, or by running `%LOCALAPPDATA%\Programs\rightfocus-parent\Uninstall-RightFocus-Parent.exe`.
- **RightFocus Child Agent (`RightFocus-Child.exe`):**
  - To prevent children from trivially disabling parental screen-time monitoring from the standard Windows Installed Apps list, the Child Agent runs silently in the background and starts via the user's Windows Startup folder (`%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup\RightFocus-Child.lnk`).
  - Parents or device owners can reconfigure pairing at any time by running:
    ```powershell
    "%LOCALAPPDATA%\Programs\rightfocus-child\RightFocus-Child.exe" --setup
    ```
  - Parents or device owners can completely uninstall the Child Agent and remove its startup entry at any time by running:
    ```powershell
    "%LOCALAPPDATA%\Programs\rightfocus-child\Uninstall-RightFocus-Child.exe"
    ```

---

## 4. Third-Party Services & Trademarks

- **Cloudflare:** Multi-device cloud sync optionally utilizes Cloudflare Workers and Cloudflare D1 under the user's own Cloudflare account, subject to [Cloudflare's Terms of Use](https://www.cloudflare.com/terms/). "Cloudflare" is a registered trademark of Cloudflare, Inc. RightFocus is an independent project and is not affiliated with or endorsed by Cloudflare, Inc.
- **Microsoft Windows & WebView2:** "Windows" and "Microsoft Edge WebView2" are trademarks of Microsoft Corporation.
- **ActivityWatch:** RightFocus's core local activity tracking and categorization concepts are inspired by [ActivityWatch](https://activitywatch.net/). RightFocus is an independent, clean-room implementation and is not affiliated with the ActivityWatch project.

---

## 5. Disclaimer of Warranties & Limitation of Liability

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, ACCURACY OF TIME TRACKING, UNINTERRUPTED SYNC DELIVERY, AND NONINFRINGEMENT.

IN NO EVENT SHALL THE AUTHORS, MAINTAINERS, OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES, DATA LOSS, OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT, OR OTHERWISE, ARISING FROM, OUT OF, OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

