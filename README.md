# OCI Policy Operator releases

This public repository contains signed, binary-only releases of OCI Policy
Operator. Application source is maintained separately in a private repository.

## Download

Open **Releases** and download only the entry point for your operating system:

- Windows: `OCI-Policy-Operator-Launcher-vX.Y.Z.exe`
- macOS: `Install-OCI-Policy-Operator-macOS.command`

On macOS, run the downloaded installer from Terminal:

```sh
sh ~/Downloads/Install-OCI-Policy-Operator-macOS.command
```

The other release assets—including `OCI-Policy-Operator-App-*`, the Python
wheel, and the JSON/signature pairs—are verified installation and update
payloads used by the Windows launcher or macOS installer. Users do not launch
those files directly.

## Update security

The Windows launcher and macOS installer embed an Ed25519 public key and accept
only matching signed manifests. They verify package SHA-256 digests and permit
downloads only from approved GitHub HTTPS hosts. The Windows launcher also
rejects unsafe archive paths and retains the last verified installed version
when an update cannot be verified. The macOS installer creates the runnable app
locally, avoiding distribution of an unnotarized application bundle.

OCI configuration, session tokens, signing keys, source code, logs, and local
runtime data are not published in this repository.
