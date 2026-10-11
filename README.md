# .github

README template and default community health files for `zyx1121` projects.

## README

Every project uses [templates/README.md](templates/README.md) in English, with [README.zh-TW.md](templates/README.zh-TW.md) and [README.zh-CN.md](templates/README.zh-CN.md) next to it. [templates/blocks.md](templates/blocks.md) holds the parts that change by project type: service, mcp, plugin, web, app, cli and research.

The page has two readers, so it has two halves:

| Part | Reader | Sections |
|------|--------|----------|
| Header | both | name, one line, badges, language switch |
| Human half | people who browse GitHub | demo, a two-sentence pitch, Features, Quick start, Usage, Configuration, How it works |
| Agent half | coding agents and LLM tools | For AI agents (a fixed list of labeled facts), Development, License |

### Content

- Each section answers one question. Delete a section that has nothing to say.
- The line under the name says what the project is and what you get, in 15 words or fewer.
- Features: 3 to 5 bullets. Each starts with a bold verb.
- Quick start is copy-paste, works in less than a minute, and ends with what you should see.
- Show the real thing: a screenshot, a GIF or real terminal output. Never show a mockup.
- No table of contents, Contributing boilerplate, acknowledgments or star-history charts. [CONTRIBUTING.md](CONTRIBUTING.md) in this repo covers every project.

### Sentences

The English follows [ASD-STE100](https://www.asd-ste100.org/) (Simplified Technical English), as adapted for agent-facing text by [asd-ste100-skill](https://github.com/danyuchn/asd-ste100-skill). A non-native reader or an agent must get one meaning from each sentence.

- One instruction per sentence. Instructions: 20 words or fewer. Descriptions: 25 words or fewer.
- Active voice and simple tenses: `hum sends`, not `is sent` or `has been sent`.
- Use the verb, not a noun made from it: `analyze`, not `perform an analysis of`.
- No phrasal verbs: `start`, not `spin up`. `use instead`, not `fall back to`.
- One name for one thing. Do not rotate synonyms.
- Numbers instead of adjectives: `7 MB`, not `tiny`. No `simple`, `fast`, `powerful`, `seamless` or `modern`.
- No semicolons, em dashes or middle dots (`·`). Write two sentences, or use a comma, a colon or parentheses.
- Paragraphs: one topic, 6 sentences or fewer. Use a list for steps and options.

Check a README before you commit it:

```sh
python3 scripts/ste-lint.py README.md
```

The Chinese translations keep the same rules where they apply: short sentences, one meaning each, and no em dashes or middle dots.

### The agent half

- The list keeps the labels and their order from the template. An agent then finds the same fact in the same place in every repo. Write `none` instead of deleting a label.
- `verify` is a command whose output proves the project works. It is not a description.
- `secrets` says what is secret and where it lives. It never contains a value.
- The rules for changing the code (where to build and test, conventions, traps) go in the repo's `AGENTS.md`.

### Header, badges, translations

- Badges: 4 or fewer, `style=flat-square`, and every badge must resolve. Dynamic shields badges do not work on private repos, so a private repo has no badges.
- Translations cover the human half. The agent half stays in English, and each translation links to it. Line 1 of a translation records the `README.md` commit that it translates, so a stale translation is easy to find.
- Header: a centered `<h1>` with the repo name. No banner image and no ASCII-art title.

## Health files

Defaults for every `zyx1121` repo that does not have its own:

| File | Covers |
|------|--------|
| [CONTRIBUTING.md](CONTRIBUTING.md) | How changes get proposed and merged |
| [SECURITY.md](SECURITY.md) | How to report a vulnerability |
| [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) | Ground rules |
| [ISSUE_TEMPLATE/](ISSUE_TEMPLATE/), [PULL_REQUEST_TEMPLATE.md](PULL_REQUEST_TEMPLATE.md) | Issue and PR forms |
