```
{ANSI Shadow: npx figlet-cli -f "ANSI Shadow" "{NAME}"
 for a visual app, skip the logo and lead with the hero screenshot instead;
 that is the stronger hook.}
```

# {Project Name}

> {Hook: the pain or the magic in one line. e.g. "Split the bill before anyone opens a calculator."}

[![CI](https://github.com/zyx1121/{repo}/actions/workflows/{ci}.yml/badge.svg)](https://github.com/zyx1121/{repo}/actions) &nbsp;[![Live](https://img.shields.io/badge/live-{domain}-111111)]({site-url}) &nbsp;[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](#license)

{Story: 2 or 3 sentences. Who keeps hitting this problem, what they did before, what this changes. No tech words yet.}

{Hero: screenshot or GIF of the real app.}
<sub>{one-line caption: what the reader is looking at}</sub>

**[Try it live]({site-url})**

## Features

- **{Verb} {object}**: {one line}
- **{Verb} {object}**: {one line}
- **{Verb} {object}**: {one line}

## Tech stack

| Layer | Choice |
|-------|--------|
| Framework | Next.js 16 (App Router) |
| Backend | Supabase |
| Styling | Tailwind CSS + shadcn/ui |
| Package manager | Bun |

## Getting started

```bash
git clone https://github.com/zyx1121/{repo} && cd {repo}
bun install
cp .env.example .env.local   # then fill in the keys below
bun dev
```

### Environment variables

| Key | Where it comes from |
|-----|---------------------|
| `NEXT_PUBLIC_SUPABASE_URL` | Supabase dashboard > Settings > API |
| `{KEY}` | {source} |

## Deploy

{One line. e.g. push to main and Vercel does the rest, or link the self-host doc.}

## Contributing

Issues and PRs welcome: start with [CONTRIBUTING.md](https://github.com/zyx1121/.github/blob/main/CONTRIBUTING.md).

## License

[MIT](LICENSE) · {something fun}
