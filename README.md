# PlainLang & `jarvis` README Website

An interactive documentation and landing page for **PlainLang** (`v4.0.0`) and **`jarvis`** (`env_jarvis.py`), built to present environment setup, `.plain` package bridge generation, dependency handling, and GitHub + `plainlang.exe` release steps in a dark developer layout.

## Features

- **Quickstart & Environment Setup**: Guides users through editable `plainlang-pkg` installation, `.pvenv` creation (`plainlang -m pvenv .pvenv`), and PowerShell activation (`Activate.ps1`).
- **`.plain` Bridge Syntax Preview**: Showcases clean `use`, `set`, `to`, and `call` statements generated inside `.pvenv/packages/<pkg>.plain` for packages and their transitive dependencies.
- **`jarvis` CLI Reference**: Documents `jarvis init`, `jarvis install`, `jarvis rebuild`, `jarvis list`, `jarvis remove` (with case-insensitive matching and `--with-deps` / `--no-deps` dependency prompts), and `jarvis info`.
- **Copy & Download Actions**: Includes one-click copy buttons for code blocks and direct `README.md` copy/download support.
- **GitHub & `plainlang.exe` Workflow**: Covers building `plainlang.exe` with PyInstaller, staging repository changes cleanly, pushing to GitHub, and attaching release binaries.

## Project Structure

```text
Programming language/
├── plainlang-pkg/          # PlainLang CLI, pvenv, and package source
│   └── src/plainlang/
│       └── env_jarvis.py   # jarvis package installer & .plain generator
├── .pvenv/                 # PlainLang environment metadata & generated modules
│   ├── packages/           # Generated *.plain files (e.g., flask.plain, numpy.plain)
│   ├── scripts/            # Environment scripts
│   ├── installed.json      # Installed package manifest
│   └── pvenv.cfg           # Environment configuration
├── index.html              # README website source
└── README.md               # Repository documentation
```

## Running the Website Locally

Save the website HTML as `index.html` and open it directly in your browser, or serve it from your project root in PowerShell:

```powershell
python -m http.server 8080
```

Then open `http://localhost:8080/index.html` in your browser.

## Building `plainlang.exe` & Pushing to GitHub

```powershell
python -m pip install --no-build-isolation --force-reinstall --no-deps -e .\plainlang-pkg
python -m PyInstaller --onefile --name plainlang .\plainlang-pkg\src\plainlang\cli.py
git status
git add .
git commit -m "Add README website and update jarvis + plainlang.exe"
git push origin main
```

Optional GitHub Release with `plainlang.exe`:

```powershell
gh release create v4.0.0 .\dist\plainlang.exe --title "PlainLang v4.0.0" --notes "Updated plainlang.exe, jarvis .plain bridges, and README website"
```
