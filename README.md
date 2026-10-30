# Arbiter

**The command center above your AI tools.**

Arbiter is a local orchestration layer for dispatching, supervising, and governing AI clients, agents, terminals, and supporting tools. It gives one operator a durable control plane without binding the workflow to a single model provider or coding client.

## Release status

Arbiter 0.1.0 is the first public pre-release, for Windows and Linux: an early build for early adopters. Download it from [Releases](https://github.com/TheAuditorTool/ArbiterMCP/releases).

Arbiter needs a license. During the pre-release it is free: ask for one at [arbitermcp.com](https://arbitermcp.com), and the email brings your key. Activate it in the app's first screen.

## Which file to download

- **Windows 10 or 11 (x64):** `Arbiter_0.1.0_x64-setup.exe` (installer) or `Arbiter_0.1.0_x64_en-US.msi`. Windows will warn that it protected your PC, because this build is not code-signed yet: choose More info, then Run anyway.
- **Linux x64:** `Arbiter_0.1.0_amd64.deb` (`sudo apt install ./Arbiter_0.1.0_amd64.deb`) or `Arbiter_0.1.0_amd64.AppImage`. Arbiter needs glibc 2.34 or newer, and the desktop app needs WebKitGTK 4.1.
- `arbiter-0.1.0-windows-x64.zip` and `arbiter-0.1.0-linux-x64.tar.gz` hold the engine alone, without the desktop app.
- **Graphics card:** the local model needs about 10 GB of graphics memory, so a card with 12 GB or more, and a driver with Vulkan support, which current NVIDIA, AMD and Intel drivers have.

macOS is not supported yet. The release notes list everything else Arbiter needs.

## Check what you downloaded

Every file is listed with its SHA256 in `arbiter-0.1.0-<os>-x64.SHA256SUMS`, signed with the Code Reality Labs release key `arbiter-release-signing-key.asc` (fingerprint `0CF6 23D6 6975 AC42 EF02 A1EA 98F3 6798 1E68 D3E3`), all attached to the release.

```
gpg --import arbiter-release-signing-key.asc
gpg --verify arbiter-0.1.0-linux-x64.SHA256SUMS.asc arbiter-0.1.0-linux-x64.SHA256SUMS
sha256sum -c --ignore-missing arbiter-0.1.0-linux-x64.SHA256SUMS
```

On Windows, `Get-FileHash .\Arbiter_0.1.0_x64-setup.exe` in PowerShell prints the SHA256 to compare with its line in `arbiter-0.1.0-windows-x64.SHA256SUMS`; GnuPG for Windows (Gpg4win) checks the signature with the same `gpg --verify` command.

## Follow development

- Product: [arbitermcp.com](https://arbitermcp.com)
- Engineering journal: [blog.arbitermcp.com](https://blog.arbitermcp.com)
- Made by: [Code Reality Labs](https://coderealitylabs.com)

## License

Arbiter is proprietary software. Copyright (C) 2026 Code Reality Labs. All rights reserved.

See [LICENSE](LICENSE) for terms. Commercial licensing and partnership inquiries:
[Code Reality Labs](https://coderealitylabs.com).
