```
{ANSI Shadow: npx figlet-cli -f "ANSI Shadow" "{NAME}"}
```

# {name}

> {Hook: what it is plus the one-line magic. e.g. "Observability for agents: OpenTelemetry in, MCP out."}

`{keyword}` · `{keyword}` · `docker` · `{keyword}`

[![CI](https://github.com/zyx1121/{repo}/actions/workflows/ci.yml/badge.svg)](https://github.com/zyx1121/{repo}/actions) &nbsp;[![Image](https://img.shields.io/badge/image-ghcr.io%2Fzyx1121%2F{repo}-111111)](https://github.com/zyx1121/{repo}/pkgs/container/{repo}) &nbsp;[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](#license)

{Story: 2 or 3 sentences. Who runs into this, what they did before, what changes once the service is running. No tech words yet.}

{Hero: one real exchange or command, verbatim, with its real output:}

```
> "{a prompt or a command someone would actually type}"
  ⚡ {tool_name} { param: "value" }
✓ {what came back, one line}
```

## What it does

- **{Verb} {object}**: {one line}
- **{Verb} {object}**: {one line}
- **{Verb} {object}**: {one line}

## Deploy

With Docker Compose, on any machine with Docker:

```sh
curl -fsSLO https://raw.githubusercontent.com/zyx1121/{repo}/main/compose.yaml
curl -fsSL -o .env https://raw.githubusercontent.com/zyx1121/{repo}/main/.env.example
# set {the required keys} in .env
docker compose up -d
```

{One or two sentences: what just started, from which image (`ghcr.io/zyx1121/{repo}`), on which ports.}

> [!IMPORTANT]
> {The one thing an operator must do before exposing it. e.g. ports listen on 127.0.0.1; put a reverse proxy with TLS in front.}

{Only if a no-Docker path exists: one line pointing at it, e.g. "Without Docker, [deploy/](deploy/) has systemd units."}

## Use

1. {First thing after it is up, e.g. create a project or a user, with the command.}
2. {Point the client or the producer at it, with the config.}
3. {The first real call.}

## Configure

Set these in `.env`; [.env.example](.env.example) documents every one.

| Key | What it sets | Default |
|-----|--------------|---------|
| `{KEY}` | {one line} | required |
| `{KEY}` | {one line} | `{value}` |

## How it works

{A small diagram (mermaid) and 2 or 3 sentences: the moving parts and the trust story, i.e. what holds which token and what can read what.}

## Develop

```sh
bun install
cp .env.example .env
{how to run it from source}
```

{Test and lint commands, the workspace layout, and one line on what CI checks: at least typecheck, lint, tests, and a smoke test that builds the image and runs the compose stack.}

## Limitations

- {known edge, one line each}

## Contributing

Issues and PRs welcome: start with [CONTRIBUTING.md](https://github.com/zyx1121/.github/blob/main/CONTRIBUTING.md).

## License

[MIT](LICENSE) · {something fun}

<!--
Every self-hosted service ships the same deploy surface, so this README can stay the same shape:

- One OCI image, ghcr.io/zyx1121/{repo}, for every role, with one entry point that picks the role.
- compose.yaml at the repo root: the service, its database if any, and one-shot jobs such as migrations, gated with service_completed_successfully. Ports bind to 127.0.0.1 by default.
- .env.example with every key, grouped into Docker Compose, every run, and a run from source.
- CI: typecheck, lint, test, then build the image and run a smoke test against a real `docker compose up`.
- Release: every push to main publishes :sha-<commit> and :main; a v* tag publishes the SemVer tags and :latest, for amd64 and arm64.
- The project page on zyx.tw uses the same sections as this README, shorter: the story as What it is, then What it does, Deploy, Use and Configure.

A host that runs containers itself (kitbash) or a desktop installer (aias) is the exception: its Deploy section says what to install instead of compose.yaml.
-->
