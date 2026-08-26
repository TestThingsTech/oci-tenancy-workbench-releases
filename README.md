# OCI Tenancy Workbench

**Explore your Tenancy.**

## Disclaimer

This project is an independent community tool published by **TestThingsTech**.
It is **not** an Oracle product, and it is not affiliated with, endorsed by, or
supported by Oracle. It is provided as-is without warranty.

The same disclaimer applies to other tools published by **TestThingsTech**.
Validate this tool in your own environment before production use.

OCI Tenancy Workbench is a local Windows and macOS utility for understanding
Oracle Cloud Infrastructure access, reviewing IAM policy configuration,
checking operational coverage, and building least-privilege policy changes.
It uses an OCI CLI session-token profile and opens its interface in your local
browser.

The application is designed for three common questions:

- **Who or what has access?** Look up an IAM user, user group, dynamic resource
  group, policy, instance, function, or other supported OCI object. Review the
  policies, grants, denies, conditions, and practical actions that apply.
- **Is the tenancy configured safely?** Scan visible policies and dynamic-group
  rules for duplicate or broader-than-needed grants, conflicting statements,
  invalid conditions, missing resources, and matching-rule problems. Run
  Oracle's OCI CIS Compliance Checker and a filterable ShowOCI inventory.
- **What is the least privilege needed?** Build a compartment-aware OCI policy
  recommendation, review the exact statement and placement, then optionally
  apply the confirmed change with a separately authorized OCI profile.

## What it can do

- Search users and OCI resources by friendly name, partial name, UPN, or OCID.
- Review user-group and dynamic-resource-group membership, matching rules, and
  every applicable Allow or Deny statement.
- Explain effective access and show examples of what a subject can and cannot
  do with its discovered permission set.
- Scan tenancy policies and dynamic groups for redundancy, excessive access,
  syntax errors, invalid OCID types, missing referenced resources, and
  meaningful Allow/Deny interactions.
- Run Oracle's OCI CIS Foundations Benchmark checker locally, retain run
  history, compare two runs, and download report ZIPs.
- Run Quick or Advanced ShowOCI inventory scans by service family, region, and
  compartment; browse counts and resource details and compare equivalent runs.
- Assess OCI Compute VM health-alarm coverage and tenancy/service announcement
  delivery through valid Notifications topics and subscriptions.
- Recommend least-privilege OCI policy statements with documented resource
  types, access levels, conditions, tenancy-aware values, and policy placement
  close to the governed resources.
- Discover existing policies that already provide the requested access so an
  unnecessary or duplicate statement is not created.

## Download and run

No GitHub account is required. Open [Releases](https://github.com/TestThingsTech/oci-tenancy-workbench-releases/releases)
and download only the entry point for your operating system.

### Windows

1. Download `OCI-Tenancy-Workbench-Launcher.exe` from the latest release.
2. Run the launcher.
3. The launcher verifies and installs the current application for your Windows
   user, then opens OCI Tenancy Workbench in the default browser.

Keep the launcher: it checks for verified updates each time it starts. The
Windows executables are not Authenticode-signed. The launcher protects its
update channel with Ed25519-signed manifests and SHA-256 package verification,
but this does not establish Windows publisher reputation.

### macOS

Download `Install-OCI-Tenancy-Workbench-macOS.command`, then run it from
Terminal:

```bash
cd ~/Downloads
chmod +x Install-OCI-Tenancy-Workbench-macOS.command
./Install-OCI-Tenancy-Workbench-macOS.command
```

If `brew --version` is unavailable and the installer says Homebrew is needed,
install Homebrew first from its official installer:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

The Workbench installer creates `~/Applications/OCI Tenancy Workbench.app` and
installs a compatible Python/Tk runtime or OCI CLI through Homebrew only when
needed. It supports Apple Silicon and Intel Macs through the locally selected
runtime. Launch the generated app after installation; it checks for verified
updates at startup.

## First launch and OCI access

1. Choose an existing OCI CLI session-token profile or create a new profile.
2. Authenticate in the browser when requested.
3. Select only the Identity Domains or tenancy areas needed for the task.
4. Review **Access requirements** in the app for the exact read-only policies
   needed by each Workbench feature.

Tenancy discovery does not begin until a valid profile is selected. Read-only
reviews do not change OCI. Policy, group, alarm, topic, subscription, or other
OCI mutations require a separate review, an explicit confirmation, and an
authenticated profile with the required change permissions.

For its standard review profile, Workbench requires a dedicated account that
cannot retrieve secret contents. It evaluates the signed-in subject's policies
and requires an effective targeted deny of `SECRET_BUNDLE_READ`; it never tests
this boundary by reading a secret payload.

## Local security and privacy

- The application and browser service run locally and bind to `127.0.0.1`.
- OCI credentials and session tokens remain in the standard local OCI profile
  directory and are not published by this repository.
- Secret payloads are never read or supplied to reports, inventory, or policy
  recommendations.
- Release manifests are Ed25519 signed and downloaded packages are SHA-256
  verified before installation.
- Closing the final Workbench browser tab shuts down the local service and its
  child-process tree.
- Reports and run history remain on the local computer unless the user chooses
  to export them.

The remaining release assets—including the Windows application ZIP, Python
wheel, updater script, and JSON/signature pairs—are installation and automatic
update payloads. Users should not launch those files directly.

## Releases and updates

Every [release page](https://github.com/TestThingsTech/oci-tenancy-workbench-releases/releases)
contains:

- the changes introduced by that version;
- Windows launch instructions;
- macOS installation commands; and
- important platform or verification notes.

The stable Windows launcher and generated macOS app check the verified release
channel at startup. If an update cannot be downloaded or verified, the last
verified installed version remains available.
