# Ignite365 — Project Context

> Handoff doc for starting a fresh chat. Read this first.
> Last updated: 2026-05-26

## What this is

**Ignite365** is a project to build tool(s) that automate tasks in **Microsoft 365**.
The specific tasks and tooling are not yet decided — see [Open Decisions](#open-decisions).

## Repo facts

| | |
|---|---|
| Local path | `/home/claw/Ignite365` |
| Remote | `git@github.com:C0deGyver/Ignite365.git` (SSH) |
| Default branch | `main` |
| State | Initial commit only (`README.md`, `LICENSE`) |
| License | **AGPL-3.0** (network-use copyleft — anyone running a modified version over a network must offer the source) |
| GitHub account | `C0deGyver` |

### GitHub auth / scopes
`gh` is authenticated as `C0deGyver` with scopes: `repo`, `read:org`, `gist`.

⚠️ **No `workflow` scope.** You cannot push files under `.github/workflows/` (GitHub Actions / CI) until this is added:
```bash
gh auth refresh -s workflow
```

## Open Decisions

These need answers before real work starts. None are decided yet — don't assume.

1. **What M365 tasks?** e.g. user/license provisioning, mailbox rules, Teams/SharePoint management, reporting, group membership, offboarding, etc. Define the first concrete tool.
2. **Tech stack?** Common options for M365 automation:
   - **Microsoft Graph API** (REST) — the modern, broadest surface.
   - **PowerShell** (`Microsoft.Graph`, `ExchangeOnlineManagement` modules) — common for admin/IT automation.
   - **Python** (`msgraph-sdk`, `msal`) or **Node** (`@microsoft/microsoft-graph-client`).
3. **Auth model?**
   - **App registration (client credentials / app-only)** for unattended automation, or
   - **Delegated (interactive/device-code)** for user-context tasks.
   - Need an Azure AD / Entra ID app registration with appropriate Graph permissions either way.
4. **Run model?** CLI tool, scheduled job, Azure Function / container, or a service?
5. **Secrets handling?** Where do client ID / tenant ID / secret or cert live? (env vars, key vault, etc.) — never commit them.

## Suggested first steps (for the fresh chat)

1. Pin down decision #1 (the first concrete task) and #2 (stack).
2. Set up an Entra ID app registration + minimal Graph permissions for that task.
3. Scaffold the project for the chosen stack (deps, config, `.gitignore` for secrets).
4. If CI is wanted, run `gh auth refresh -s workflow` first.

## Environment notes

- Working on host `openclaw`, Linux. `gh` and `git` available.
- This file lives in the repo root; update it as decisions get made.
