# Third-Party Libraries and Licenses Inventory

Review date: 2026-03-13

This document summarizes the libraries used in this project, the executable packaging toolchain, and the licensing impact for distributing binaries while keeping the source code private.

## 1. Direct project dependencies

### Frontend (`frontend/package.json`)

| Package | Declared version | Resolved version | Type | License |
|---|---:|---:|---|---|
| @angular/common | ^17.3.0 | 17.3.12 | runtime | MIT |
| @angular/compiler | ^17.3.0 | 17.3.12 | runtime | MIT |
| @angular/core | ^17.3.0 | 17.3.12 | runtime | MIT |
| @angular/forms | ^17.3.0 | 17.3.12 | runtime | MIT |
| @angular/platform-browser | ^17.3.0 | 17.3.12 | runtime | MIT |
| @angular/platform-browser-dynamic | ^17.3.0 | 17.3.12 | runtime | MIT |
| @angular/animations | ^17.3.0 | 17.3.12 | runtime | MIT |
| rxjs | ^7.8.1 | 7.8.2 | runtime | Apache-2.0 |
| zone.js | ^0.14.4 | 0.14.10 | runtime | MIT |
| @angular/cli | ^17.3.0 | 17.3.17 | dev/build | MIT |
| @angular/compiler-cli | ^17.3.0 | 17.3.12 | dev/build | MIT |
| @angular-devkit/build-angular | ^17.3.0 | 17.3.17 | dev/build | MIT |
| typescript | ^5.3.3 | 5.4.5 | dev/build | Apache-2.0 |

### Desktop (`desktop/package.json`)

| Package | Declared version | Resolved version | Type | License |
|---|---:|---:|---|---|
| electron | ^30.0.0 | 30.5.1 | dev/build | MIT |
| electron-builder | ^24.13.3 | 24.13.3 | packaging | MIT |

### Backend (`backend/requirements.txt` + build scripts)

| Package | Declared version | Installed version | Type | License |
|---|---:|---:|---|---|
| fastapi | ==0.110.0 | 0.110.0 | runtime | MIT (classifier) |
| uvicorn | ==0.27.1 | 0.27.1 | runtime | BSD (classifier) |
| pydantic | ==2.6.1 | 2.6.1 | runtime | MIT (classifier) |
| python-multipart | ==0.0.9 | 0.0.9 | runtime | Apache-2.0 (classifier) |
| basyx-python-sdk | >=2.0.0 | 2.0.0 | runtime | MIT (classifier) |
| pyinstaller | (installed by build script) | 6.19.0 | packaging | GPLv2+ with PyInstaller exception |

## 2. Transitive dependencies (full inventory)

A full inventory was generated from local installed dependencies:

- `frontend`: 756 packages (`frontend/thirdparty-licenses-node_modules.csv`)
- `desktop`: 266 packages (`desktop/thirdparty-licenses-node_modules.csv`)
- `backend` Python: 26 packages (`backend/thirdparty-licenses-python.csv`)

Combined total (name+version): 926 packages.

## 3. License-sensitive dependencies

Detected:

- `pyinstaller` (GPLv2 or later) with an explicit exception that permits packaging and distributing non-free software.
- `pyinstaller-hooks-contrib` includes mixed licensing (GPL-2.0-or-later / Apache-2.0 depending on hook type).
- `node-forge` appears as dual license `(BSD-3-Clause OR GPL-2.0)`; compliance can be achieved through the BSD-3-Clause option.

## 4. Can we distribute executables with private source code?

Technical OSS licensing conclusion (not legal advice): **yes, this is viable** with the current dependency set.

No AGPL dependency or strong copyleft dependency was detected that would force publication of the application's source code.

## 5. Recommended distribution obligations

1. Include a third-party notices file in the installer or next to the executable.
2. Include the applicable license texts (MIT, Apache-2.0, BSD, ISC, etc.).
3. Preserve copyright and NOTICE attributions where required (especially Apache-2.0).
4. Keep a versioned dependency inventory per release.

## 6. Artifacts already generated in this repository

- `third_party/THIRD_PARTY_NOTICES.md`
- `third_party/license_texts/manifest.csv`
- `third_party/license_texts/*` (copied license texts detected for direct dependencies and packaging tools)

To regenerate these artifacts:

```powershell
powershell -ExecutionPolicy Bypass -File .\scripts\collect-third-party-license-files.ps1
```

## 7. Internal sources used for this report

- `frontend/package.json`
- `desktop/package.json`
- `backend/requirements.txt`
- `scripts/build-backend.ps1`
- `scripts/build-desktop.ps1`
- `scripts/build-portable.ps1`
- `frontend/thirdparty-licenses-node_modules.csv`
- `desktop/thirdparty-licenses-node_modules.csv`
- `backend/thirdparty-licenses-python.csv`
- `third_party/license_texts/manifest.csv`

## 8. Note

This document should be reviewed for every release, because dependency updates can change licensing and obligations.
