# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| Latest stable (0.2.x) | Yes |
| Older versions | Please update |

## Reporting a Vulnerability

**Do not file public issues for security vulnerabilities.**

Please report security issues by emailing: **security@axyome.ai**

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Any suggested mitigations (optional)

You will receive an acknowledgment within 48 hours and a resolution timeline within 7 days.

## Security Design Principles

Axyome XM is designed with security in mind:

- **Limited network egress** - The MCP server makes no network calls. The extension talks to `api.axyome.ai` only while you are signed in (sign-in, licence, devices; cloud sync on Team & Enterprise plans)
- **Local-first storage** - Captured data is persisted locally in `%APPDATA%\Code\User\globalStorage\axyome.axyome-xm\`
- **Secret redaction** - Terminal capture automatically redacts tokens, keys, and passwords before storage
- **No code execution** - The extension never executes user code or eval() arbitrary input
- **Sandboxed MCP server** - The MCP binary runs as a stdio process with no open ports
- **VSIX integrity** - All platform binaries are hash-validated during build and installation

## Scope

In-scope for responsible disclosure:
- Extension code execution vulnerabilities
- Injection via MCP tool parameters
- Unauthorized file system access outside globalStorage
- Secret leakage via terminal capture
- MCP server privilege escalation

Out of scope:
- VS Code itself (report to Microsoft)
- GitHub Copilot (report to GitHub)
- Social engineering
