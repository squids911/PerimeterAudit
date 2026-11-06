# Perimeter Audit

Windows GUI utility for authorized external perimeter inventory.

## Current capabilities
- TCP connect scan for custom ports and ranges.
- Basic service hints and simple service banners.
- Preliminary UDP probes for DNS and NTP; generic UDP checks are explicitly marked as inconclusive when no response is received.
- TLS 1.2/1.3 handshake and certificate details on supported TLS ports.
- HTML and CSV reports, local JSON scan history, and scan cancellation.

## Build outputs
GitHub Actions builds two Windows x64 deliverables:
- **PerimeterAudit.exe** — self-contained single-file portable executable.
- **PerimeterAudit-Setup.exe** — Inno Setup installer.

Builds run on pushes to `main` and `develop`, and on version tags (`v*`). Version tags also create a GitHub Release with both deliverables attached.

## Local build
Requirements: Windows 10/11 x64 and .NET 8 SDK.

```powershell
Set-ExecutionPolicy -Scope Process Bypass
.\publish.ps1
```

The portable executable is written to `publish\PerimeterAudit.exe`.

## Safety and limitations
Use only against systems you own or are explicitly authorized to assess. This is an inventory tool, not a full vulnerability scanner or a replacement for Nmap. UDP silence is not proof that a port is closed. The application does not brute-force credentials, exploit vulnerabilities, or change target configuration.
