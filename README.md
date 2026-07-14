# SpaceBox Lite

Official release builds for **SpaceBox Lite** — the client app for **SpaceDrop**, a many-to-one, end-to-end-encrypted file drop service.

- A **host** signs in with a SpaceBox account and receives files.
- **Senders** need no account: they pair with a host by scanning a QR code and can then drop files to it. No personal information is collected from senders.
- Every file is encrypted **on the sender's device** with post-quantum cryptography (ML-KEM-768 key encapsulation + AES-256-GCM) before it is uploaded. The server only ever stores ciphertext, and the host's private key never leaves the host's device.

> **Note:** This repository hosts release binaries and documentation only. The application source code is not public.

## Download

Grab the latest version from the [**Releases**](../../releases/latest) page.

| Platform | File | Notes |
|----------|------|-------|
| Android  | `*.apk` | 64-bit devices (arm64-v8a / x86_64), Android 7.0+ |
| macOS    | `*.dmg` | Universal (Apple Silicon + Intel), signed & notarized |
| Windows  | `*.msix` | x64, code-signed |
| Linux    | `*.run` | x64, self-contained installer |

iOS builds are not distributed through this repository.

## Installation

### Android

Download the APK and open it. If prompted, allow your browser or file manager to install unknown apps (Settings → Apps → Special app access → Install unknown apps). The APK is signed with our release key, so future versions install directly over the old one.

### macOS

Open the DMG and drag **SpaceBox Lite** into **Applications**. The app is signed with a Developer ID certificate and notarized by Apple, so it opens without warnings.

### Windows

Double-click the MSIX package and click **Install**. The package is code-signed (Azure Trusted Signing), so Windows App Installer accepts it directly. Requires Windows 10 (build 17763) or later, x64.

### Linux

Download the `.run` file, make it executable, and run it — it launches the installer:

```bash
chmod +x SpaceBoxLite-*-linux-x64.run
./SpaceBoxLite-*-linux-x64.run
```

Secure key storage requires `libsecret` and a running keyring (GNOME Keyring or KWallet). On Ubuntu/Debian:

```bash
sudo apt install libsecret-1-0 libjsoncpp25
```

## Verifying your download

Each release includes a `SHA256SUMS` file. After downloading, verify with:

```bash
sha256sum -c SHA256SUMS --ignore-missing
```

The macOS and Windows binaries are additionally covered by their platform code signatures (notarization / Trusted Signing).

## Reporting problems

Found a bug or an installation issue? [Open an issue](../../issues) in this repository. Please include your platform, app version, and what you were doing when the problem occurred — but **never attach private keys, pairing QR codes, or session tokens**.

## Legal

SpaceBox Lite is proprietary software, © i46. The binaries are provided as-is for end-user installation; redistribution of modified packages is not permitted.
