# UML AASX Studio - Public Distribution

This repository is the **public distribution channel** for UML AASX Studio.

## Application screenshots

UML diagram edited in the desktop app:

![UML AASX Studio UI](docs/images/uml-aasx-studio.png)

AASX package opened after export from the same diagram:

![UML AASX Studio Exported AASX](docs/images/uml-aasx-studio-exportaasx.png)

## What is included

- Windows installer releases (`.exe`) in **GitHub Releases**.
- SHA-256 checksum files (`.sha256`) for release integrity verification.
- Third-party license and notice files required for distribution.

## Download and install

1. Go to the **Releases** page.
2. Download the latest installer: `UML-AASX-Studio-Setup-<version>.exe`.
3. Download the matching `.sha256` checksum file.
4. Optionally verify the checksum.
5. Run the installer and follow the setup steps.

## Windows security warning (SmartScreen)

If Windows shows a security warning, the application may not yet have established SmartScreen reputation.

- Click **More info** → **Run anyway** only if you downloaded the installer from this official repository.
- Verify the SHA-256 checksum before running the installer.

## Verify file integrity

PowerShell example:

```powershell
Get-FileHash .\UML-AASX-Studio-Setup-<version>.exe -Algorithm SHA256
