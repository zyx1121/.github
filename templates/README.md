<!--
README template v2: https://github.com/zyx1121/.github/blob/main/templates/README.md
Keep the section order. Delete any section the project does not need, and every
comment like this one. Never ship a {placeholder}.
Install, Quick start and Usage variants per project type: templates/blocks.md.
README.zh-TW.md and README.zh-CN.md translate the sections above "For AI agents".
-->

<div align="center">

<h1>{name}</h1>

<p><strong>{What it is and what you get, in one line under 15 words.}</strong></p>

<!-- At most 4 badges, flat-square, every one must resolve. Private repos: no dynamic badges. -->
[![CI](https://img.shields.io/github/actions/workflow/status/zyx1121/{repo}/ci.yml?branch=main&style=flat-square&label=CI)](https://github.com/zyx1121/{repo}/actions)
[![Release](https://img.shields.io/github/v/release/zyx1121/{repo}?style=flat-square&sort=semver)](https://github.com/zyx1121/{repo}/releases)
[![License](https://img.shields.io/github/license/zyx1121/{repo}?style=flat-square)](LICENSE)

**English** | [繁體中文](README.zh-TW.md) | [简体中文](README.zh-CN.md)

</div>

<!-- The real thing, not a mockup: a screenshot, a short GIF, or a terminal exchange
     with its real output. -->
{demo}

{Who needs this and what changes once it runs. Two sentences at most.}

## Features

- **{Verb} {object}**: {what it does for you, one line}
- **{Verb} {object}**: {one line}
- **{Verb} {object}**: {one line}

## Quick start

```sh
{the shortest copy-paste path from nothing to working, under a minute}
```

{One line: what you should see.}

## Usage

{The 2 to 4 things people actually do with it, each with the exact command or click.}

## Configuration

| Key | Sets | Default |
|-----|------|---------|
| `{KEY}` | {one line} | required |

## How it works

```mermaid
flowchart LR
  A[{input}] --> B[{name}] --> C[{output}]
```

{The moving parts in 2 or 3 sentences, including what holds which secret.}

## For AI agents

Facts for coding agents and LLM tools. The rules for changing the code are in [AGENTS.md](AGENTS.md).

<!-- Keep every label and its order. Write "none" when a label does not apply. -->
- **Summary**: {one sentence}
- **Type**: {service, mcp, plugin, web, app, cli, library or research}
- **Interfaces**: {CLI `command`, MCP `name` (stdio), HTTP `base URL`, or none}
- **Install**: `{one command}`
- **Run**: `{one command}`
- **Verify**: `{a command whose output proves it works}`
- **Config**: {`ENV_VAR` names, or none}
- **Secrets**: {what is secret and where it lives, never the value, or none}
- **Limits**: {known limits, one short sentence each}

## Development

```sh
git clone https://github.com/zyx1121/{repo} && cd {repo}
{install}
{test}
```

{What CI runs, in one line.}

## License

[MIT](LICENSE)
