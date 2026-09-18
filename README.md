<div align="center">

# 🌿 Leaf

### **Make more of what you read.**

**A private, local-first workspace for reading, deep research, drafting, study, notes, and translation.**

[![Release](https://img.shields.io/github/v/release/ChrisBakhit/leaf-releases?color=2ea44f&label=Release)](https://github.com/ChrisBakhit/leaf-releases/releases/latest)
[![Platform](https://img.shields.io/badge/Platform-Windows%20x64-blue)](#downloads)
[![License](https://img.shields.io/badge/License-Proprietary-informational)](#license--security)
[![Privacy](https://img.shields.io/badge/Privacy-100%25%20Local--First-success)](#privacy--architecture)

<br/>

[📥 Download for Windows](https://github.com/ChrisBakhit/leaf-releases/releases/latest) · [📋 Release Notes](https://github.com/ChrisBakhit/leaf-releases/releases) · [🌐 Web Workspace](https://leaf.local/workspace) · [💬 Report Issue](https://github.com/ChrisBakhit/leaf-releases/issues)

</div>

---

## ⚡ Highlights

- **🔒 100% Local-First & Private**: Your library, indexed books, and database remain on your local machine. No unwanted cloud indexing or corporate telemetry.
- **📚 Grounded Research & Citations**: Ask your entire book collection or paper library complex questions with verifiable citations linking directly to exact pages and passages.
- **🔎 Multilingual Vector & Hybrid Search**: Full OCR text-layer generation with multi-dimensional vector chunking and fast FTS5 keyword indexing.
- **✍️ Notes, Study & Translation**: Integrated rich-text notebook, flashcards, automated quiz generation, and inline quote translation.
- **📱 Secure Multi-Device Pairing**: Connect desktop, tablet, and mobile clients across your home network or via end-to-end encrypted relay without public port forwarding.

---

## 📥 Downloads & Installation

| Platform | Version | Status | Download Link |
| :--- | :--- | :--- | :--- |
| **Windows 10 / 11 (x64)** | `0.1.14` | **Stable** | [Leaf-Setup-0.1.14-x64.exe](https://github.com/ChrisBakhit/leaf-releases/releases/latest/download/Leaf-Setup-0.1.14-x64.exe) |
| **macOS (Apple Silicon & Intel)** | `—` | *Coming Soon* | *In Pilot Testing* |
| **Linux (.AppImage / .deb)** | `—` | *Coming Soon* | *In Pilot Testing* |
| **Mobile & Tablet (iOS / Android)** | `—` | *Coming Soon* | *In Pilot Testing* |

### Quick Start (Windows)
1. Download `Leaf-Setup-0.1.14-x64.exe`.
2. Run the installer to place Leaf on your PC.
3. Launch Leaf — your local host initializes automatically.

---

## 🏗 Architecture & Privacy

```
┌──────────────────────────────────────────────────────────┐
│                      Your Computer                       │
│                                                          │
│   ┌───────────────────┐        ┌───────────────────────┐ │
│   │   Leaf Desktop    │ ◄────► │    Leaf Local Host    │ │
│   │    Application    │  IPC   │   (FastAPI + SQLite)  │ │
│   └───────────────────┘        └───────────┬───────────┘ │
│                                            │             │
│                                    Local DB & Files      │
│                                            │             │
│                                 ┌──────────▼───────────┐ │
│                                 │   data/leaf.db       │ │
│                                 │   library/ (PDF/EPUB)│ │
│                                 └──────────────────────┘ │
└────────────────────────────────────────────▲─────────────┘
                                             │
                       End-to-End Encrypted  │  (Zero Knowledge)
                       Relay WebSocket       │
                                             │
                                 ┌───────────▼───────────┐
                                 │   Mobile / Tablets    │
                                 │     (Pair Client)     │
                                 └───────────────────────┘
```

- **Local Storage**: Everything is stored in SQLite (`leaf.db`) and local files (`library/`).
- **Encrypted Secrets**: Sensitive tokens use OS-level DPAPI / Keychain (`safeStorage`).
- **Zero-Knowledge Pairing**: Remote relay connections authenticate via signed challenge transcripts; intermediate relays never hold plaintext data or keys.

---

## 🔄 Automatic Updates

Leaf includes an integrated updater. Once installed, the application checks this public releases channel for new versions automatically without requiring a GitHub account.

You can inspect all changes in the [Release History](https://github.com/ChrisBakhit/leaf-releases/releases).

---

## 🛡 License & Security

- **Software License**: Leaf binaries are distributed under proprietary terms. Third-party libraries and fonts retain their respective open-source licenses (MIT, Apache 2.0, OFL).
- **Security Inquiries**: To report security vulnerabilities or bugs, please open an issue in the [Leaf Releases Issue Tracker](https://github.com/ChrisBakhit/leaf-releases/issues).
