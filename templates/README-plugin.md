```
{ANSI Shadow: npx figlet-cli -f "ANSI Shadow" "{NAME}"
 name too long, or a visual plugin? skip the logo and lead with a real demo
 block (terminal output / screenshot / GIF) instead; that is the stronger hook.}
```

# {plugin-name}

> {One-line tagline: what it is + the Claude-native hook. e.g. "A Claude-native X for Claude Code: compose it from small components, and let Claude read, vet, and tune them for you."}

`{keyword}` · `{keyword}` · `{keyword}` · `{keyword}`

[![Claude Code plugin](https://img.shields.io/badge/Claude%20Code-plugin-d97757)]({repo-url}) &nbsp;[![Live demo](https://img.shields.io/badge/demo-{site}-111111)]({site-url}) &nbsp;[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](#license)

{Hero: a real demo block (the plugin's actual output / a screenshot / a GIF) + a one-line `<sub>` caption. For a visual plugin, lead with this; it beats any logo art.}

{Story: 2 or 3 sentences. The itch that made you build it, and what using it feels like. Keep it above the fold; a reader who stops here should still want it.}

## Install

```
/plugin marketplace add {owner}/{repo}
/plugin install {plugin}@{marketplace}
{/your:setup, if the plugin needs one-time wiring}
```

{One sentence on what setup does / why it's needed.} {If there's a site, point at it: browse and preview at **[{site}]({site-url})**.}

## {What it gives you}

{The components / commands / capabilities: a table or bold-lead bullets, each one line.}

| {thing} | {kind} | {what it does} |
|---------|--------|----------------|
| `{id}`  | …      | …              |

## The Claude-native angle

{The differentiator: keep it ABOVE contributor detail. What the manifest/contract declares (inputs, requires, capabilities, config), and which slash commands lean on it:}

- **`/{plugin}:install <x>`**: Claude reads the source, summarises what it does / what it touches / what it needs, confirms, then installs.
- **`/{plugin}:configure` · `/{plugin}:preview` · `/{plugin}:doctor`**: tune, dry-run, health-check.

## {Extending it}

{Concise overview of how to author a piece, two-or-three sentences. Link the full contract/spec rather than inlining it.} Full contract: [`spec/CONTRACT.md`](…), schemas in [`spec/`](…).

<details>
<summary><b><code>{manifest}.json</code> at a glance</b></summary>

```jsonc
{ /* the minimal manifest, annotated */ }
```

{One line on the security boundary / what authored code can and can't see.}

</details>

## Contributing

{If the marketplace is federated, make that the primary path and label the built-in route as secondary:}

New components are welcome. The marketplace is **federated**, so the usual path keeps your component in **your own repo** and just indexes it here:

1. Put it under `components/<id>/` in a repo of your own ({manifest}, renderer, `README.md`, `preview`).
2. Add your repo as a source in [`registry.json`](registry.json) and open a PR.

CI validates every submission; once merged the site lists it and users install it with `/{plugin}:install <id>`. To contribute into the **official built-in set** instead, PR it directly under [`{plugin-dir}/components/<id>/`](…) here. General ground rules live in [CONTRIBUTING.md](https://github.com/zyx1121/.github/blob/main/CONTRIBUTING.md).

## License

[MIT](LICENSE) · {something fun}
