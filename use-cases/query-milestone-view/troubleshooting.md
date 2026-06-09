# Troubleshooting: MSX MCP Server Setup

Real-world gotchas encountered during setup, with fixes.

---

## 1. `npx` hangs indefinitely when testing the server

**Symptom:** Running `npx -y @microsoft/msx-mcp-server@latest --help` or `--version` never returns — the process just hangs.

**Why:** The MSX MCP server is a **stdio MCP server**, not a CLI tool. When launched, it immediately starts listening on stdin for MCP protocol messages. There is no `--help` or `--version` flag — it just blocks waiting for input.

**Fix:** Don't test the server by running it directly. Instead, verify the package exists with:

```sh
npm view @microsoft/msx-mcp-server version
```

This should return something like `0.5.1` in under 5 seconds. If it returns a version, the package is reachable and the setup will work.

To confirm the server is working in Clawpilot, restart the app and run `crm_whoami`.

---

## 2. `npm` can't find `@microsoft/msx-mcp-server` — 404 Not Found

**Symptom:**
```
npm error 404 Not Found - GET https://registry.npmjs.org/@microsoft%2fmsx-mcp-server
npm error 404  '@microsoft/msx-mcp-server@latest' is not in this registry.
```

**Why:** The package is on **GitHub's npm registry** (`npm.pkg.github.com`), not the public npmjs.com registry. Without an explicit scope mapping, npm looks in the wrong place.

**Fix:** Add this line to `~/.npmrc`:

```
@microsoft:registry=https://npm.pkg.github.com
```

Do **not** just set `registry=https://npm.pkg.github.com` globally — that breaks all other npm packages. Only scope `@microsoft` to GitHub.

---

## 3. `.npmrc` line gets concatenated to the previous line

**Symptom:** After using `Add-Content` (PowerShell) or `echo >>` (cmd) to append to `.npmrc`, the new line gets joined to the last existing line:

```
# Before (no trailing newline):
registry=https://registry.npmjs.org/

# After Add-Content "newline":
registry=https://registry.npmjs.org/@microsoft:registry=https://npm.pkg.github.com
```

This breaks both entries and npm ignores the malformed line.

**Why:** `.npmrc` files often lack a trailing newline. `Add-Content` appends without checking.

**Fix:** Rewrite the entire `.npmrc` cleanly using a heredoc instead of appending:

```powershell
$npmrc = @"
//npm.pkg.github.com/:_authToken=YOUR_TOKEN_HERE
@jinlee794:registry=https://npm.pkg.github.com
@microsoft:registry=https://npm.pkg.github.com
registry=https://registry.npmjs.org/
"@
Set-Content "$env:USERPROFILE\.npmrc" $npmrc
```

Always verify after writing:
```powershell
Get-Content "$env:USERPROFILE\.npmrc" -Raw
```

---

## 4. Auth token already exists — don't create a new one

**Symptom:** You already have a GitHub PAT in `.npmrc` for another `@scope` (e.g., `@jinlee794`).

**Key insight:** The `//npm.pkg.github.com/:_authToken` entry is **registry-scoped**, not package-scoped. A single auth token authenticates you for **all packages** on `npm.pkg.github.com` regardless of which `@scope` owns them.

If you see this in your `.npmrc`:
```
//npm.pkg.github.com/:_authToken=gho_...
@jinlee794:registry=https://npm.pkg.github.com
```

You **do not** need a new PAT. Just add:
```
@microsoft:registry=https://npm.pkg.github.com
```

Verify existing auth works:
```sh
npm whoami --registry=https://npm.pkg.github.com
```
If that returns your GitHub username, you're already authenticated.

---

## 5. Clawpilot `m-mcp-servers.json` format differs from standard MCP JSON

**Symptom:** The repo README shows a generic MCP JSON format (`"type": "stdio"`), but Clawpilot uses a different wrapper structure.

**Generic MCP format (as shown in README):**
```json
{
  "msx": {
    "type": "stdio",
    "command": "npx",
    "args": ["-y", "@microsoft/msx-mcp-server@latest"],
    "env": { "npm_config_@microsoft:registry": "https://npm.pkg.github.com" }
  }
}
```

**Clawpilot `m-mcp-servers.json` format (what actually works):**
```json
{
  "servers": {
    "msx": {
      "builtin": false,
      "config": {
        "name": "MSX CRM",
        "type": "command",
        "command": "npx",
        "args": ["-y", "@microsoft/msx-mcp-server@latest"],
        "env": {
          "npm_config_@microsoft:registry": "https://npm.pkg.github.com"
        }
      },
      "tools": []
    }
  }
}
```

Key differences:
- Wrapped inside a `"servers"` object
- Each server has `"builtin": false`, a `"config"` sub-object, and an empty `"tools"` array
- `"type"` is `"command"` (not `"stdio"`)
- The `env` block lives inside `"config"`

File location: `~/.copilot/m-mcp-servers.json`

---

## 6. `env` block in MCP config is required — don't skip it

**Why it matters:** Even if your `.npmrc` has `@microsoft:registry=https://npm.pkg.github.com`, when Clawpilot launches the MCP server process it may use a clean environment. The `env` block in the server config ensures `npx` always knows to look at GitHub's registry for `@microsoft/*` packages, regardless of the shell environment.

```json
"env": {
  "npm_config_@microsoft:registry": "https://npm.pkg.github.com"
}
```

This is the env-variable equivalent of the `.npmrc` scope setting. Always include it.
