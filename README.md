# wuwa-quest-tracker

Offline Wuthering Waves quest tracker generator.

This repository reads user-provided SQLite database files and generates a static
HTML quest checklist page. It does not include Pak extraction, key acquisition,
process injection, runtime hooks, local game path discovery, or game automation.

## Required Inputs

Prepare these files yourself before running the generator:

- Quest config databases: `db_quest.db`, `db_QuestData.db`, `db_questtype.db`
- Simplified Chinese text databases: one or more `lang_multi_text*.db`

The generator only reads the paths passed through CLI arguments.

## Generate HTML

Run from the repository root:

```bash
python -m Tools \
  --quest-db /path/to/db_quest.db \
  --questdata-db /path/to/db_QuestData.db \
  --questtype-db /path/to/db_questtype.db \
  --multitext-db /path/to/lang_multi_text.db \
  --multitext-db /path/to/lang_multi_text_1sthalf.db \
  --out docs/quest_tracker_zh.html
```

The generated page is a self-contained static HTML file:

```text
docs/quest_tracker_zh.html
```

## Arguments

- `--quest-db`: path to `db_quest.db`
- `--questdata-db`: path to `db_QuestData.db`
- `--questtype-db`: path to `db_questtype.db`
- `--multitext-db`: path to `lang_multi_text*.db`; can be passed multiple times
- `--out`: output HTML path; defaults to `out/quest_tracker_zh.html`
- `--root`: output root; defaults to the current directory

## Public Deployment

The GitHub workflow for this repository should deploy only static files from
`docs/`. It should not run extraction, key acquisition, runtime automation, or DB
generation jobs.
