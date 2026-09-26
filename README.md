# KiteScribe - Windows transcription and OCR releases

Official public distribution mirror for KiteScribe by FXBG Foundry LLC, developed by [Caymran Cummings](https://github.com/caymran) (Caymran Coral Cummings).

- This repository contains release artifacts only (installers, hashes, release notes).
- Source code is maintained in a private repository.

# 🧠 KiteScribe
**Developer:** [Caymran Cummings](https://github.com/caymran), [FXBG Foundry LLC](https://fxbgfoundry.com/)  
**License:** Proprietary (see EULA.md)  

![License: Proprietary](https://img.shields.io/badge/License-Proprietary-blue.svg)  

---

## 🎯 Overview
**KiteScribe** is a standalone transcription and visual capture tool that:
- Records system audio in real-time (loopback).  
- Captures screenshots of an active window periodically.  
- Conducts **speech-to-text** transcription.  
- Performs **on-screen text recognition**.  
- Runs as a focused live transcription + screen OCR desktop app.  

---

## ⚙️ Features
| Category | Description |
|-----------|--------------|
| **Audio Capture** | Live loopback audio transcription. |
| **Speech Recognition** | Offline English transcription. |
| **OCR** | Extracts text from periodic screenshots. |
| **Logging** | Unified on-screen and file logging under `logs/`. |
| **Installer** | Packaged as a per-user MSI installer (no elevation required), with Start Menu + desktop shortcuts and bundled README. |
| **Portable** | Bundled with all necessary packages for standalone operation without install. |

---

## 🖥️ Installation
1. **Download the installer**  
   From the [official GitHub Releases](https://github.com/FXBGFoundry/kitescribe-releases/releases) page:
   ```
   KiteScribe-UserSetup.msi
   ```
   > Defaults to `%LOCALAPPDATA%\KiteScribe` (you can choose a different folder during setup).

2. **License Acceptance (Installer)**  
   During MSI installation you must accept the in-wizard EULA (`installer/EULA.rtf`) before the install can proceed.

3. **First Run**  
   The app checks for license - if exists waits for audio and captures screen when user selection is made.
   If license is not found - offers 5 minute trial - as well as instructs user on how to obtain/install license.
   
---

## 🔏 Release Signing
GitHub Actions now performs **DigiCert EV signing only for tag releases** (`refs/tags/v*`) to preserve the signing quota. 
- After signing, the workflow runs `signtool verify` against both `KiteScribe.exe` and `KiteScribe-UserSetup.msi` and fails the run if verification fails.

## 🚀 Usage Guide
### 1️⃣ Start the Application
Launch from the Start Menu or desktop shortcut.  

### 2️⃣ Select Audio Source
Choose **Loopback** device from which to transcribe system sound.

### 3️⃣ Pick a Window
Click **🎯 Select Target Window** and choose any active window.  

### 4️⃣ Transcription
Speech and OCR results appear live in the app panes.

### 5️⃣ Exit Behavior
Closing the app stops capture.

---

## 🔐 Offline License Workflow
KiteScribe now enforces an **offline signed license** at startup.

### Runtime behavior
- The app looks for `kitescribe.license` next to `KiteScribe.exe`, then falls back to `%LOCALAPPDATA%/KiteScribe/license/kitescribe.license`.
- If no valid license exists, the app enters a 5-minute trial mode and then stops transcription while preserving transcript copy/export of captured text.
- A license is bound to a single machine fingerprint.
- A anti-rollback guard rejects license on backwards clock movement.

---

## 📬 Contact
📧 [KiteScribe Sales](mailto:sales@kitescribe.ai)  
🌐 [KiteScribe.ai](https://KiteScribe.ai)

Tag builds also generate an SBOM at `out/KiteScribe.sbom.cdx.json` plus a bundled-binaries manifest (`out/THIRD_PARTY_BINARIES.txt`) and attach them to the GitHub Release assets.

## Developer and related work

[Caymran Cummings](https://github.com/caymran) develops KiteScribe at [FXBG Foundry](https://fxbgfoundry.com/). See [ScheduleBrief Viewer](https://github.com/FXBGFoundry/schedulebrief-releases) for a Windows tool for viewing project schedules.
