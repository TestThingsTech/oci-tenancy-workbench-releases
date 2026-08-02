# OCI Policy Operator releases

This public repository contains signed, binary-only releases of OCI Policy
Operator. Application source is maintained separately in a private repository.

## Download

Open **Releases** and download the versioned Windows launcher named:

`OCI-Policy-Operator-vX.Y.Z.exe` for Windows, or the versioned macOS Intel or
Apple-silicon launcher archive.

The files named `OCI-Policy-Operator-App-*`, `release.json`, and
`release.json.sig` are verified automatic-update payloads used by the launcher.

## Update security

The launcher embeds an Ed25519 public key and accepts only a matching signed
manifest. It verifies the package SHA-256, permits downloads only from GitHub
HTTPS hosts, rejects unsafe archive paths and links, and retains the last
verified installed version when an update cannot be verified.

OCI configuration, session tokens, signing keys, source code, logs, and local
runtime data are not published in this repository.
