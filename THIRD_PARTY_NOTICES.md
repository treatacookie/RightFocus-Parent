# Third-Party Notices & Open-Source Attributions

**RightFocus Parent** and **RightFocus Child Agent** are built on top of open-source software and redistributable runtime components. We gratefully acknowledge the authors and maintainers of the following projects.

---

## 1. Conceptual Inspiration

### ActivityWatch
- **Website:** [https://activitywatch.net/](https://activitywatch.net/)
- **Source Repository:** [https://github.com/ActivityWatch/activitywatch](https://github.com/ActivityWatch/activitywatch)
- **License of ActivityWatch:** Mozilla Public License 2.0 (MPL-2.0)
- **Attribution Note:** RightFocus's core local activity tracking and regex categorization concepts are inspired by ActivityWatch. RightFocus (`RightFocus-Parent` and `RightFocus-Child`) is a 100% clean-room implementation written from scratch in Rust, Tauri v2, and React 19 + TypeScript, with zero source code copied from ActivityWatch.

---

## 2. Application Framework & Frontend Libraries

### Tauri (v2)
- **Source:** [https://github.com/tauri-apps/tauri](https://github.com/tauri-apps/tauri)
- **License:** MIT OR Apache-2.0
- **Copyright:** Copyright (c) 2019 - present, The Tauri Programme within The Commons Conservancy.

### React & React DOM (v19)
- **Source:** [https://github.com/facebook/react](https://github.com/facebook/react)
- **License:** MIT
- **Copyright:** Copyright (c) Meta Platforms, Inc. and affiliates.

### Recharts (v2)
- **Source:** [https://github.com/recharts/recharts](https://github.com/recharts/recharts)
- **License:** MIT
- **Copyright:** Copyright (c) 2015-present Recharts Group.

---

## 3. Rust Crates & Embedded Database

### SQLite (via `rusqlite` / `libsqlite3-sys` bundled)
- **Source:** [https://www.sqlite.org/](https://www.sqlite.org/) / [https://github.com/rusqlite/rusqlite](https://github.com/rusqlite/rusqlite)
- **License:** SQLite is in the **Public Domain**. `rusqlite` is licensed under the **MIT License** (Copyright (c) 2014-2026 The rusqlite developers).

### Rust Cryptography & Serialization Crates
- **`aes-gcm` & `sha2` (RustCrypto):** Licensed under MIT OR Apache-2.0.
- **`serde` & `serde_json`:** Licensed under MIT OR Apache-2.0 (Copyright (c) Erick Tryzelaar and David Tolnay).
- **`ureq`:** Licensed under MIT OR Apache-2.0 (Copyright (c) Martin Algesten).
- **`flate2`:** Licensed under MIT OR Apache-2.0.
- **`base64`:** Licensed under MIT OR Apache-2.0.
- **`chrono`:** Licensed under MIT OR Apache-2.0.
- **`regex`:** Licensed under MIT OR Apache-2.0 (Copyright (c) The Rust Project Developers).
- **`windows-sys`:** Licensed under MIT OR Apache-2.0 (Copyright (c) Microsoft Corporation).
- **`rfd` (Rusty File Dialogs):** Licensed under MIT.

---

## 4. Microsoft Edge WebView2 Loader (`WebView2Loader.dll`)

`RightFocus-Parent` uses the Windows system WebView2 runtime via `WebView2Loader.dll` (distributed by Microsoft Corporation as part of the Microsoft Edge WebView2 SDK):

```text
Copyright (c) Microsoft Corporation. All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are
met:

   * Redistributions of source code must retain the above copyright
notice, this list of conditions and the following disclaimer.
   * Redistributions in binary form must reproduce the above
copyright notice, this list of conditions and the following disclaimer
in the documentation and/or other materials provided with the
distribution.
   * The name of Microsoft Corporation, or the names of its contributors
may not be used to endorse or promote products derived from this
software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
"AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

