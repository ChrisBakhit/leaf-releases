<div align="center">

# 🌿 Leaf

### **The Private, Local-First & Cloud-Synced Research & Study Workspace**

**Read, research, draft, study, transcribe, and translate across all your documents — with verified source citations, multilingual OCR, and zero cloud lock-in.**

[![Release](https://img.shields.io/github/v/release/ChrisBakhit/leaf-releases?color=2ea44f&label=Release)](https://github.com/ChrisBakhit/leaf-releases/releases/latest)
[![Platform](https://img.shields.io/badge/Platform-Windows%20x64%20%7C%20Web%20%7C%20Cloud-blue)](#downloads--apps)
[![Security](https://img.shields.io/badge/Security-E2EE%20Relay%20%2B%20RLS-success)](#hybrid-local--cloud-architecture)
[![License](https://img.shields.io/badge/License-Proprietary-informational)](#license--security)

<br/>

[📥 Download Windows App](https://github.com/ChrisBakhit/leaf-releases/releases/latest) · [🌐 Launch Web Workspace](https://leaf.local/workspace) · [☁️ Cloud Sign-In](https://leaf.local/account.html) · [📋 Release History](https://github.com/ChrisBakhit/leaf-releases/releases) · [💬 Issues](https://github.com/ChrisBakhit/leaf-releases/issues)

</div>

---

## ⚡ Comprehensive Feature Breakdown

### 📚 1. Advanced Reading & Document Management
- **Universal Format Support**: Ingest and render PDF, EPUB, DOCX, Markdown, plain text, and HTML.
- **Selectable OCR & Geometry Layer**: Scanned documents automatically undergo high-precision OCR (via Tesseract) producing selectable, searchable word bounding boxes even on degraded physical scans.
- **Paged & Continuous Reader Modes**: Switch seamlessly between book-style dual/single page turns and infinite continuous scroll.
- **Highlights, Bookmarks & Annotations**: Add persistent layered color highlights, margin notes, and passage bookmarks that link directly back to exact page coordinates.

---

### 🔬 2. Deep Research & Grounded AI Citations
- **Source-Grounded Answering**: Ask questions across your entire library simultaneously. Leaf retrieves relevant chunk candidates and provides syntheses with exact paragraph-level citations.
- **Multilingual Vector & Keyword Search**: Combines Dense Vector retrieval (multilingual embeddings) with BM25/FTS5 SQLite full-text keyword indexing for precision recall.
- **Citation Analysis & Verification**: Direct interactive jump-links from citations back to highlighted source passages in original books or PDFs.
- **AI Profile Flexibility**: Bring your own keys with OpenRouter or connect directly to local OpenAI-compatible endpoints (Ollama, LM Studio, vLLM).

---

### ✍️ 3. Notebook, Drafting & Study System
- **Rich-Text Notebook (TipTap DOM)**: Structured notes with inline block formatting, image embedding, tags, and bi-directional linking.
- **Drafting Studio**: AI-assisted long-form writing with citation back-propagation, section re-ordering, and live evidence boards.
- **Automated Study Cards & Quizzes**: Automatically transform entire chapters or tagged passages into active recall flashcards and comprehension quizzes.
- **Real-Time Quote Translation**: Translate excerpts in place with side-by-side linguistic breakdown.
- **Audio & Handwritten Capture**: Transcribe audio notes or digitize handwritten journal pages into searchable text.

---

### ☁️ 4. Hybrid Local-First & Cloud Ecosystem
- **Self-Hosted / 100% Local Mode**: Run locally with Docker (`docker compose up --build`) or natively with embedded SQLite. No internet connection or cloud account required.
- **Encrypted Cloud Sync & Identity**: Connect via OIDC (Auth0 / Supabase Auth) with strict PostgreSQL Row-Level Security (RLS) guaranteeing tenant isolation.
- **Zero-Knowledge Device Pairing**: Pair phone and tablet clients across networks via an end-to-end encrypted Cloudflare Worker relay without public port forwarding or router modifications.
- **OS Safe Storage**: Passwords hashed with `scrypt` ($N=16384$), session tokens stored as SHA-256 digests, and client tokens protected via Windows DPAPI / macOS Keychain.

---

## 🏗 Hybrid Architecture Overview

```
                          ┌───────────────────────────┐
                          │    Leaf Cloud (Optional)  │
                          │  • OIDC Auth0 / Supabase  │
                          │  • PostgreSQL RLS Storage │
                          └─────────────▲─────────────┘
                                        │  Encrypted Sync
                                        │
┌───────────────────────────────────────┼────────────────────────────────────────┐
│  Local Workstation                    │                                        │
│                                       │                                        │
│   ┌──────────────────────────┐        │        ┌──────────────────────────┐    │
│   │       Leaf Desktop       │ ◄──────┴──────► │     Leaf Local Host      │    │
│   │    (Electron / React)    │  Secure IPC     │   (FastAPI + SQLite WAL) │    │
│   └──────────────────────────┘                 └─────────────┬────────────┘    │
│                                                              │                 │
│                                                        Local Filesystem        │
│                                                              │                 │
│                                                 ┌────────────▼────────────┐    │
│                                                 │  data/leaf.db           │    │
│                                                 │  library/ (PDFs/EPUBs)  │    │
│                                                 └─────────────────────────┘    │
└──────────────────────────────────────────────────────────────▲─────────────────┘
                                                               │
                                      End-to-End Encrypted     │  (Zero-Knowledge
                                      WebSocket Relay          │   64KB Frames)
                                                               │
                                                 ┌─────────────▼────────────┐
                                                 │    Mobile / Tablets      │
                                                 │   (Expo / React Native)  │
                                                 └──────────────────────────┘
```

---

## 📥 Downloads & Apps

| Client | Version | Platform | Status | Download Link |
| :--- | :--- | :--- | :--- | :--- |
| **Windows Desktop** | `0.1.14` | Windows 10 / 11 (x64) | **Stable** | [Download Installer (.exe)](https://github.com/ChrisBakhit/leaf-releases/releases/latest/download/Leaf-Setup-0.1.14-x64.exe) |
| **Web Workspace** | `0.1.14` | Modern Browsers | **Live** | [Open Web Client](https://leaf.local/workspace) |
| **macOS Desktop** | `0.1.14` | macOS (Apple Silicon / Intel) | *In Testing* | *Release Candidate* |
| **Linux Client** | `0.1.14` | Linux (AppImage / .deb) | *In Testing* | *Release Candidate* |
| **Mobile & Tablet** | `0.1.14` | iOS & Android | *In Testing* | *Expo Client* |

---

## 🚀 Quick Start Guide

### Desktop Client (Windows)
1. Download [Leaf-Setup-0.1.14-x64.exe](https://github.com/ChrisBakhit/leaf-releases/releases/latest/download/Leaf-Setup-0.1.14-x64.exe).
2. Run the installer and launch **Leaf**.
3. Drag & drop your PDF, EPUB, or Markdown files into the library to begin reading and indexing.

### Self-Hosted Docker Host
For team servers or headless home servers:
```powershell
git clone https://github.com/ChrisBakhit/leaf-studio.git
cd leaf-studio
docker compose up --build
```
Your local host is live at `http://127.0.0.1:8000`.

---

## 🛡 Security & Verification

- **Integrity**: Every release includes SHA-256 and SHA-512 cryptographic digests in `latest.yml` alongside differential `.blockmap` files for delta updates.
- **Sandboxing**: Renderer processes run in isolated contexts with context isolation enabled and explicit IPC allowlists.
- **Reporting Vulnerabilities**: Submit security issues via [GitHub Issue Tracker](https://github.com/ChrisBakhit/leaf-releases/issues).
