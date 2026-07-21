```
{ANSI Shadow: npx figlet-cli -f "ANSI Shadow" "{NAME}"}
```

# @zyx1121/{name}-mcp

> {Hook: one line of pain or magic, not a feature list. e.g. "Stop alt-tabbing into {App Name}. Just ask."}

[![npm](https://img.shields.io/npm/v/@zyx1121/{name}-mcp?color=cb3837)](https://www.npmjs.com/package/@zyx1121/{name}-mcp) &nbsp;[![CI](https://github.com/zyx1121/{repo}/actions/workflows/{ci}.yml/badge.svg)](https://github.com/zyx1121/{repo}/actions) &nbsp;[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](#license)

{Story: 2 or 3 sentences. The itch (what you kept doing by hand), the turn (what changes now that Claude can reach {App Name}), the payoff (what a day with it feels like). Write it like you are telling a friend, not listing features.}

{Hero: one real exchange, verbatim. In a CLI world this is your screenshot:}

```
> "{a prompt someone would actually type}"
  ⚡ {tool_name} { param: "value" }
✓ {what came back, one line}
```

## What it does

- **{Verb} {object}**: {one line}
- **{Verb} {object}**: {one line}
- **{Verb} {object}**: {one line}

## Quickstart

```bash
claude mcp add {name} -- npx @zyx1121/{name}-mcp
```

Any other MCP client:

```jsonc
{
  "mcpServers": {
    "{name}": { "command": "npx", "args": ["@zyx1121/{name}-mcp"] }
  }
}
```

> [!NOTE]
> Needs Node.js >= 18 and macOS with {App Name} configured.
> First run prompts for Automation permission (System Settings > Privacy & Security > Automation).

## Tools

| Tool | Description |
|------|-------------|
| `tool_name` | {what it does, and when Claude reaches for it} |

## Examples

| You say | Claude runs |
|---------|-------------|
| "{prompt}" | `tool_name { param: "value" }` |

## How it works

{2 or 3 sentences: the moving parts and the trust story. e.g. plain AppleScript via `osascript`, no daemon, no network, nothing leaves the machine.}

## Limitations

- macOS only (uses AppleScript via `osascript`)
- {known edge, one line each}

## Contributing

Issues and PRs welcome: start with [CONTRIBUTING.md](https://github.com/zyx1121/.github/blob/main/CONTRIBUTING.md).

## License

[MIT](LICENSE) · {something fun}
