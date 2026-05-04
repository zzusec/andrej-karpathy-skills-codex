# andrej-karpathy-skills-codex

A Codex `AGENTS.md` adaptation of coding-agent behavior guidelines inspired by Andrej Karpathy's observations on common LLM coding mistakes.

This repository is intended for OpenAI Codex/Codex CLI users who want a lightweight project instruction file that encourages:

- thinking before editing,
- simple implementations,
- precise diffs,
- goal-driven verification.

## Installation

This project is not a Claude Code plugin. It is a Codex/Codex CLI instruction file. Install it by placing `AGENTS.md` in the project where you run Codex.

### Option 1: Install directly into one project

Use this when the target project does not already have an `AGENTS.md` file.

```bash
cd /path/to/your/project
curl -L -o AGENTS.md https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md
codex
```

### Option 2: Merge into an existing `AGENTS.md`

Use this when your project already has custom Codex instructions. Review the result afterward and remove any duplicate or conflicting rules.

```bash
cd /path/to/your/project
printf '\n\n# andrej-karpathy-skills-codex\n\n' >> AGENTS.md
curl -L https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md >> AGENTS.md
```

### Option 3: Install from a cloned repository

Use this if you want to review or edit the rules before copying them into a project.

```bash
git clone https://github.com/zzusec/andrej-karpathy-skills-codex.git
cd andrej-karpathy-skills-codex
cp AGENTS.md /path/to/your/project/AGENTS.md
```

### Option 4: Use it for all projects under one parent directory

Use this when all of your projects live under the same parent directory, such as `~/work`, `~/projects`, or your home directory.

Put one shared `AGENTS.md` in the parent directory:

```bash
cd /path/to/parent-directory
curl -L -o AGENTS.md https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md
```

Example directory layout:

```text
work/AGENTS.md
work/project-a/
work/project-b/
work/project-c/
```

Then start Codex from any child project:

```bash
cd /path/to/parent-directory/project-a
codex
```

If your Codex setup loads instructions from parent directories, every child project can use the same shared rules.

For example, if all projects are under your home directory:

```bash
cd ~
curl -L -o AGENTS.md https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md
```

Then projects like these can share the same parent `AGENTS.md`:

```text
~/AGENTS.md
~/project-a/
~/project-b/
~/project-c/
```

### Option 5: Copy it into every project root

Use this for maximum compatibility, especially if your Codex setup does not load parent-directory instructions.

```text
project-a/AGENTS.md
project-b/AGENTS.md
project-c/AGENTS.md
```

You can copy the file manually, or use a shell loop after reviewing the target directories:

```bash
for project in /path/to/projects/*; do
  if [ -d "$project" ] && [ ! -f "$project/AGENTS.md" ]; then
    cp AGENTS.md "$project/AGENTS.md"
  fi
done
```

If a project already has its own `AGENTS.md`, merge the rules manually instead of overwriting it.

### Verify installation

After installation, confirm the file exists in the project where you start Codex:

```bash
cd /path/to/your/project
ls AGENTS.md
codex
```

When Codex starts, ask it to summarize the active project instructions or confirm that it can see `AGENTS.md`.

### Update later

To replace your local copy with the latest version:

```bash
cd /path/to/your/project
curl -L -o AGENTS.md https://raw.githubusercontent.com/zzusec/andrej-karpathy-skills-codex/main/AGENTS.md
```

If you previously merged these rules into a custom `AGENTS.md`, update manually instead of overwriting the whole file.

## Files

- `AGENTS.md` — Codex-ready project instructions.
- `NOTICE.md` — source and attribution notes.

## Attribution

This is a Codex-oriented adaptation of ideas from `forrestchang/andrej-karpathy-skills`, whose README describes the project as MIT licensed and derived from Andrej Karpathy's public observations.

## License

MIT. See `LICENSE`.
