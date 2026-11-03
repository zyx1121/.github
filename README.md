# .github

README template, default community health files and shared workflows for `zyx1121` projects.

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

## Repo settings and About

Every repo uses the same settings. Apply them when you create a repo:

```sh
gh repo create zyx1121/{repo} --public --description "{the README one line}"
gh api -X PATCH repos/zyx1121/{repo} -F allow_squash_merge=true -F allow_merge_commit=false \
  -F allow_rebase_merge=false -F delete_branch_on_merge=true -F has_wiki=false -F has_projects=false
```

- Merge: squash only, and GitHub deletes the branch after the merge.
- Wiki and Projects: off. Turn Projects on only for a repo that has a linked project board.
- Description: the one line from the README, in English, with no em dash or middle dot.
- Website: a live site only. Leave it empty when there is none, and do not point it at the Releases page.
- Topics: 3 to 5 lowercase words. Use one type word (`self-hosted`, `claude-code-plugin`, `mcp`, `website`, `macos-app`, `cli`, `research`, `course-project`), then the main technology and the domain.
- License: MIT for every public repo.

## Health files

Defaults for every `zyx1121` repo that does not have its own:

| File | Covers |
|------|--------|
| [CONTRIBUTING.md](CONTRIBUTING.md) | How changes get proposed and merged |
| [SECURITY.md](SECURITY.md) | How to report a vulnerability |
| [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) | Ground rules |
| [ISSUE_TEMPLATE/](ISSUE_TEMPLATE/), [PULL_REQUEST_TEMPLATE.md](PULL_REQUEST_TEMPLATE.md) | Issue and PR forms |

## Shared workflows

| Workflow | Does |
|------|--------|
| [alint.yml](.github/workflows/alint.yml) | Fails a pull request whose added lines break an alint grep rule ([zyx1121/plugin](https://github.com/zyx1121/plugin) `skills/alint`) |
| [image.yml](.github/workflows/image.yml) | Builds a repo's images once per commit with a registry cache, runs its smoke test, and pushes each as `candidate-<tree>` |
| [promote.yml](.github/workflows/promote.yml) | Makes the candidates `tree-<tree>` after every check passed |
| [ship.yml](.github/workflows/ship.yml) | On push to main, retags the `tree-` images `sha-<commit>` and `main`, then deploys them. It never builds |

A repo calls it with one file:

```yaml
# .github/workflows/alint.yml
name: alint
on:
  pull_request:
jobs:
  alint:
    uses: zyx1121/.github/.github/workflows/alint.yml@main
    # with:
    #   runs-on: '["self-hosted","carrel"]'
    #   container: node:22
```

### Deploy a service

A service ships only images that its ci passed, and it builds each image once. The pull request builds it, so the merge only retags and deploys it: portal went from 228 s to 42 s from merge to live. The tag `tree-<git tree>` names the files, not the commit. A pull request checks out its merge with main, so its tree is the tree the squash merge has.

1. `deploy/smoke.sh` starts the stack from the `<name>:ci` images and probes it.
2. `deploy/carrel-start.sh` reads `VERSION` (`sha-<commit>`), installs `compose.yaml` and starts the stack. It reports ready when web is healthy.
3. `compose.yaml` runs web with `init: true`, `stop_grace_period: 3s`, and a healthcheck with `start_interval: 1s`.
4. The app reads its commit at run time (for example from `VERSION` in `.env`), not at build time. The image is built before the merge commit exists.
5. A build that needs a secret reads it with `RUN --mount=type=secret,id=NAME,env=NAME`. The image job passes it under `secrets: build-env:` as a JSON object, each value written with `toJSON` so a multi-line value survives: `{"NAME": ${{ toJSON(secrets.NAME) }}}`. `secrets: inherit` does not cross organizations. Its value never lands in a layer, but what the build writes with it does, and `buildcache` keeps every stage: delete such files (for example `.next/cache`) in the same `RUN`. Forks and Dependabot build without secrets.

```yaml
# .github/workflows/ci.yml
name: ci
on:
  pull_request:
  push:
    branches: [main]
jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
      # the repo's own lint, typecheck and tests
  image:
    uses: zyx1121/.github/.github/workflows/image.yml@main
    permissions:
      contents: read
      packages: write
    with:
      images: '[{"name": "ghcr.io/<owner>/<repo>"}]'
      smoke: bash deploy/smoke.sh
  promote:
    needs: [check, image]
    uses: zyx1121/.github/.github/workflows/promote.yml@main
    permissions:
      contents: read
      packages: write
    with:
      images: '["ghcr.io/<owner>/<repo>"]'
```

```yaml
# .github/workflows/release.yml
name: release
on:
  push:
    branches: [main]
jobs:
  ship:
    uses: zyx1121/.github/.github/workflows/ship.yml@main
    permissions:
      contents: read
      packages: write
      actions: read
      id-token: write
    with:
      images: '["ghcr.io/<owner>/<repo>"]'
      tenant: <carrel tenant>
      app: <carrel app>
```

