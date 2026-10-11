# Blocks by project type

[README.md](README.md) is the same for every project. What changes by type is the badge set, Quick start, Usage and the `interfaces` in "For AI agents". Pick one block and paste it over those parts.

## service

Self-hosted systems that run as containers.

Badges: CI, `[![Image](https://img.shields.io/badge/ghcr.io-zyx1121%2F{repo}-111111?style=flat-square&logo=docker&logoColor=white)](https://github.com/zyx1121/{repo}/pkgs/container/{repo})`, License.

````markdown
## Quick start

```sh
curl -fsSLO https://raw.githubusercontent.com/zyx1121/{repo}/main/compose.yaml
curl -fsSL -o .env https://raw.githubusercontent.com/zyx1121/{repo}/main/.env.example
docker compose up -d
```

{What started, from `ghcr.io/zyx1121/{repo}`, on which port.}

> [!IMPORTANT]
> {The one thing to do before exposing it, e.g. ports bind to 127.0.0.1, put TLS in front.}
````

The deploy surface every service ships, so this block stays true:

- One image, `ghcr.io/zyx1121/{repo}`, for every role. One entry point selects the role.
- `compose.yaml` at the root with the service, its database if any, and one-shot jobs such as migrations gated with `service_completed_successfully`. Ports bind to 127.0.0.1.
- `.env.example` with every key.
- CI: typecheck, lint, test, then build the image and smoke-test a real `docker compose up`.
- Release: each push to main publishes `:sha-<commit>` and `:main`. A `v*` tag publishes the SemVer tags and `:latest`, for amd64 and arm64.

A host that runs containers itself or a desktop installer is the exception: Quick start says what to install instead.

## mcp

MCP servers.

Badges: CI, npm or Release, `[![MCP](https://img.shields.io/badge/MCP-server-000000?style=flat-square)](https://modelcontextprotocol.io)`, License.

````markdown
## Quick start

```sh
claude mcp add {name} -- npx @zyx1121/{name}-mcp
```

Any other MCP client:

```json
{ "mcpServers": { "{name}": { "command": "npx", "args": ["@zyx1121/{name}-mcp"] } } }
```

## Usage

| You ask | It calls |
|---------|----------|
| "{a real prompt}" | `{tool} { "param": "value" }` |

## Tools

| Tool | Does | Writes? |
|------|------|---------|
| `{tool}` | {one line} | {read / write / destroy} |
````

`interfaces.mcp` in the agent block: `{name} (stdio)` or `{url} (streamable HTTP)`.

## plugin

Claude Code or Codex plugins, distributed through `zyx1121/marketplace`.

Badges: CI, Release, `[![Claude Code](https://img.shields.io/badge/Claude_Code-plugin-D97757?style=flat-square)](https://github.com/zyx1121/marketplace)`, License.

````markdown
## Quick start

```sh
claude plugin marketplace add zyx1121/marketplace
claude plugin install {name}@zyx1121
```

Codex: `codex plugin add {name}@zyx1121`.

## Usage

| Component | Name | What it does |
|-----------|------|--------------|
| skill | `{name}` | {one line} |
| MCP tool | `{tool}` | {one line} |
````

## web

Websites and web apps.

Badges: CI, `[![Live](https://img.shields.io/badge/live-{domain}-000000?style=flat-square)](https://{domain})`, License.

````markdown
{Screenshot of the real page, light and dark if it has both.}

## Quick start

Open [{domain}](https://{domain}).

To run it locally:

```sh
bun install && cp .env.example .env && bun dev
```
````

## app

iOS, macOS or desktop apps.

Badges: CI, Release, platform (`[![macOS](https://img.shields.io/badge/macOS-15%2B-000000?style=flat-square&logo=apple)](#)`), License.

````markdown
{Screenshot or a 10-second GIF of the main flow.}

## Quick start

Download the latest build from [Releases](https://github.com/zyx1121/{repo}/releases), or build it:

```sh
{build command}
```
````

## cli

Command-line tools and libraries.

Badges: CI, Release or package registry, License.

````markdown
## Quick start

```sh
{install command}
{name} {the one command people run first}
```

```text
{its real output}
```
````

## research

Papers, theses and experiments.

Badges: none, or a paper link (`[![Paper](https://img.shields.io/badge/paper-PDF-b31b1b?style=flat-square)]({url})`).

````markdown
{The one figure or result that matters, with a one-line caption.}

## Reproduce

```sh
{setup}
{the command that regenerates the result}
```

{Hardware it needs and how long it takes.}

## Cite

```bibtex
{bibtex}
```
````

In the agent block, `type` is `research`, every `interfaces` key is usually `none`, and `verify` is the reproduce command.
