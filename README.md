# PlainLang Download Website

Official download portal and documentation site for **PlainLang (`v4.0.0`)** — a standalone plain-English programming language, **PlainLang Studio** IDE, and the **`jarvis`** package manager.

## Overview

This website provides end-users and developers with direct downloads for Windows (`plainlang.exe` CLI and the x64 Windows Installer with `.plain` file association), alongside quickstart guides for `.pvenv` virtual environments and `.plain` package bridges.

## Key Website Sections

- **Hero & Direct Downloads**:
  - **PlainLang Windows x64 (`plainlang.exe`)** — Standalone CLI runtime for executing `.plain` scripts directly from PowerShell or Command Prompt.
  - **PlainLang Studio & Setup Installer (`PlainLang-Setup-x64.exe`)** — Desktop Tkinter IDE with syntax autofill, automatic system `PATH` registration, and `.plain` double-click file association.
- **Interactive `.plain` Code Showcase**: Demonstrates zero-syntax plain-English code (`use`, `set`, `to`, `call`) and auto-generated `.plain` bridges for Python/PyPI packages.
- **Quickstart & `jarvis` Package Guide**: Step-by-step instructions for initializing `.pvenv`, installing packages with dependencies into `.plain`, and managing environments.
- **Release & Checksum Info**: Version notes, system requirements (Windows 10/11 x64), and direct links to GitHub Releases.

## Project Structure

```text
plainlang-download-site/
├── index.html              # Main download landing page & interactive docs
├── assets/                 # Logos, screenshots, and UI styles/scripts
├── releases/               # Optional local release binaries or links to GitHub Releases
│   └── plainlang.exe
└── README.md               # Website documentation
```

## Local Preview

Run a local static server from the website directory in PowerShell:

```powershell
python -m http.server 8080
```

Open `http://localhost:8080` in your browser to preview the download page.

## Linking `plainlang.exe` Releases on GitHub

1. **Build the standalone executable** from the PlainLang source directory:
   ```powershell
   python -m PyInstaller --onefile --name plainlang .\plainlang-pkg\src\plainlang\cli.py
   ```
2. **Publish the release binary** via GitHub CLI (`gh`):
   ```powershell
   gh release create v4.0.0 .\dist\plainlang.exe --title "PlainLang v4.0.0" --notes "Standalone plainlang.exe with jarvis dependency .plain bridges"
   ```
3. **Update the download button URL** in `index.html` to point to the release asset:
   ```html
   <a href="[https://github.com/bookmyticket2009-web/PlainLang/releases/latest/download/plainlang.exe](https://github.com/bookmyticket2009-web/PlainLang/releases/latest/download/plainlang.exe)" download>
     Download plainlang.exe (Windows x64)
   </a>
   ```

## Deploying the Website

- **GitHub Pages**: Push `index.html` to your repository's `main` branch (or `docs/` folder) and enable **Settings → Pages → Deploy from a branch**.
- **Static Hosts (Render / Vercel / Netlify)**: Deploy directly as a static site with `.` as the publish directory.

## Post-Install Quickstart (For Users Downloading PlainLang)

```powershell
# Verify installation
plainlang --version

# Initialize a PlainLang environment
jarvis init

# Install a package and generate .plain files with dependencies
jarvis install flask

# Run a PlainLang script
plainlang app.plain
```
