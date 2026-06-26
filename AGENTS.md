# AGENTS.md — OpenHarmony docs repo

## What this repo is
OpenHarmony developer documentation — markdown only. No source code, no build, no tests, no `package.json`.

## Host and platform
- Hosted on **GitCode** (Gitee ecosystem): `https://gitcode.com/openharmony/docs`
- PR template: `.gitcode/PULL_REQUEST_TEMPLATE.zh-CN.md`
- License: CC-BY-4.0 for documents; Apache 2.0 for code/config files

## Key directories
- `zh-cn/` — Chinese docs (primary, most content lives here)
  - `application-dev/` — App development docs
  - `device-dev/` — Device development docs
  - `release-notes/` — Version release notes
  - `contribute/` — Contribution guides, style guide, templates, markdown checks
  - `design/` — API & subsystem design reference
- `en/` — English docs (mirrors zh-cn structure, **lags behind zh-cn**)
- `docker/` — Docker env for building OpenHarmony itself (not this repo)
- `.config/` — CI check profiles & whitelists
- `skill/` — Glossary extraction and batch-fix skills (see dedicated sections)
- `CODEOWNERS` — Per-file owner mapping (~5600 lines, per-doc granularity)

## Active branches and SDK versions
From `.config/Profiles.json` (the authoritative source):
| Branch | SDK Version / API Level |
|--------|------------------------|
| master | 20 (OpenHarmony 6.0 Release) |
| OpenHarmony-5.1.0-Release | 18 |

The PR template also requires tracking sync to these active branches (no SDK mapping in Profiles.json):
- OpenHarmony_feature_sta_20260331
- OpenHarmony-7.0-Beta1 (API 26.0.0 Beta1)
- weekly_20260309 (API 24 Beta)

**API docs must match the SDK version of the target branch.**

## Skills (`skill/`)

### Glossary extraction (`skill/glossary_skill.md`)
When user asks to "提取术语并生成术语解释" or similar:
1. Read `skill/glossary_skill.md` for full rules — do not guess.
2. Input: target doc list from `skill/responsibility.txt`; external SDK at `/home/w30042390/oh/interface/sdk-js` (used to exclude API class/interface/decorator names). **This path may not exist in all environments** — if missing, ask the user.
3. Output: write glossary to `zh-cn/application-dev/ui/arkui-glossary.md`.
4. Reference example: `zh-cn/glossary.md`.
5. Key exclusion rules: no overly broad terms (e.g. "数据"), no industry-common terms, no API element names from SDK, no device/board names, no arbitrary English abbreviations.
6. Term format: "English full name (abbreviation); Chinese full name", sorted by English first letter.
7. Report stats: total terms found, processed count, remaining count with reasons.

### Batch-fix from detection results (`skill/SKILL_common.md`, `skill/apply_common_fixes.py`)
When user has an Excel/CSV detection result file and wants to apply `suggestion` fixes to source docs:
1. Read `skill/SKILL_common.md` for the full workflow.
2. The script `skill/apply_common_fixes.py` parses suggestions from ` ```suggestion ``` ` code blocks in Excel content columns, locates target lines with multi-strategy search, applies fixes, and writes results back to Excel.
3. Three-round processing: standard search → improved search → aggressive search for remaining failures.
4. After modification, a **verification step** must run (step 8 in SKILL_common.md) to confirm each fix actually landed correctly.

## File naming and structure conventions
- File names: `xxx-xxx.md` (lowercase, hyphenated). No spaces, no uppercase.
- Directory index files: use `Readme-CN.md` (Chinese) / `Readme-EN.md` (English), not `readme.md`.
- Images: store in `figures/` or `pic/` (Chinese) / `pic-en/` (English) sibling to the doc. Reference with relative paths.
- Image formats: only png, jpg, gif, jpeg, svg allowed (CI check rejects other formats).
- Topic IDs: docs use `#ZH-CN_TOPIC_...` anchor IDs in headings — **never change these**.
- Always start new docs from a template in `zh-cn/contribute/template/` (guide, tutorial, FAQ, ts, native, js, errorcodes, etc.)

## Important HTML comment conventions (CI-checked)

Docs use several HTML comment tags that an agent must preserve and not accidentally remove:

- **`<!--no_check-->`** — placed at end of a doc to skip all CI markdown checks. Only use where explicitly needed.
- **Metadata header comments** — docs start with ownership metadata; never change these:
  ```
  <!--Kit: Kit Name-->
  <!--Subsystem: Subsystem-->
  <!--Owner: @username-->
  <!--Designer: @username-->
  <!--Tester: @username-->
  <!--Adviser: @username-->
  ```
- **`<!--Del-->` / `<!--DelEnd-->`** — deletion markers used in Readme-CN.md and API docs to mark content that should be hidden on the website (typically system APIs). The visible text goes between the tags; the hidden link/text goes inside `<!--Del-->`. Preserve exactly.
- **`<!--RP1-->` / `<!--RP1End-->`** — release plan markers for new content sections. Numbered per doc (RP1, RP2…). Preserve exactly.
- **urlpath comments in Readme navigation** — Readme node links use `<!--urlpath-slug-->` after the link text, where the slug is lowercase, ≤50 chars, only letters/digits-hyphens-underscores:
  ```
  - 入门<!--application-getting-started-->
    - 快速入门<!--quick-start-->
      - [开发准备](quick-start/start-overview.md)
  ```
  CI validates these are unique per Readme and match the format rules.

## Admonition patterns
`public_sys-resources/` directories contain icon GIFs at multiple directory levels. Use relative paths from the doc's location:
- `icon-note.gif` → `> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**`
- `icon-caution.gif` → `> ![icon-caution.gif](public_sys-resources/icon-caution.gif) **注意：**`
- `icon-notice.gif` → `> ![icon-notice.gif](public_sys-resources/icon-notice.gif) **须知：**`
- `icon-danger.gif` → `> ![icon-danger.gif](public_sys-resources/icon-danger.gif) **警告：**`
- `icon-tip.gif` → tip, `icon-warning.gif` → warning

**Admonitions cannot contain code blocks, tables, or images (icons excepted).** Put code blocks in regular body text instead.

## Markdown style rules (CI-checked, highest-signal)

From `zh-cn/contribute/markdown-check/md-style-check.md` and style guide. These are the rules most commonly broken:

**Indentation:**
- Ordered list sub-content: indent **3 spaces** (not 2 or 4).
- Unordered list sub-content: indent **2 spaces**.
- Code blocks inside ordered lists: indent 3 spaces. Inside unordered lists: indent 2 spaces.

**Code blocks:**
- Triple-backtick fences with language tag (` ```ts`, ` ```c`, etc.) — no bare ` ``` `.
- No 4-space indented code blocks (CI flags these).
- Example code: `console.info` or `console.error` only — **never `console.log`** (CI rejects it).

**Headings:**
- Max 3 levels. Action docs use verb-object titles (e.g., "申请权限").
- No numbered headings (e.g., "1.1 Name", "一、Name") — CI flags these.

**Tables:**
- ≤9 rows, ≤4 columns. Left-aligned. No empty cells (use "无" or "不涉及").
- No tab characters. Every row starts and ends with `|`.
- Separator: `|---|` with no spaces between dashes.

**Links:**
- Pure markdown `[text](url)` — no HTML `<a>` tags.
- No raw URLs as text. Link to documents directly, not to their `#一级标题` anchor.

**Admonitions in tables/cells:**
- "说明"/"注意" must be on standalone blockquote line or end with `<br/>` if inline.
- In table cells, "说明"/"注意" must have `<br/>` before them.

**Other:**
- `<br/>`, `<br>`, `<sup>` must be properly closed.
- Paragraph separation: blank line, not two trailing spaces.
- Unordered lists: `- ` only (not `* ` or `+ `).
- List items: 2–9 recommended; max 2 nesting levels.

## PR requirements
- **Change source**: exactly ONE — 新增需求 / 变更需求 / 问题修复 / 主动优化 — with a tracking number. Never mix sources in one PR.
- **DCO sign-off**: every commit needs `Signed-off-by: Name <email>` in the commit message.
- **Self-check**: API docs must match the SDK version. Example code must be tested on real devices when possible; provide compile and runtime log screenshots.
- **CI gates**: sensitive word scan, markdown style check, OAT/SCANOSS compliance, CleanCode static analysis, API reference link validation, sample code accuracy check.

## Git LFS tracked types
From `.gitattributes` — these file types require Git LFS. Do not commit them directly:
`.tgz .trp .apk .jar .mp4 .zip .asm .8svn .9svn .dylib .exe .a .so .bin .dll`

## Critical "do not" rules (the ones agents most often violate)
- Do not change topic IDs (`ZH-CN_TOPIC_...`), metadata HTML comments, or `<!--Del-->`/`<!--RP-->` tags.
- Do not put code blocks, tables, or images inside admonition blockquotes.
- Do not use `console.log` in example code.
- Do not use 4-space indented code blocks or bare ``` without language tag.
- Do not use numbered headings.
- Do not use 2-space indent for ordered list sub-content (use 3-space).
- Do not use 3-space indent for unordered list sub-content (use 2-space).
- Do not edit `en/` docs without corresponding `zh-cn/` changes.
- Do not mix multiple change sources in one PR.
- Do not commit binary assets directly (use Git LFS).
- Do not add code, build scripts, or `package.json`.

## Key reference files
| File | Purpose |
|------|---------|
| `zh-cn/contribute/markdown-check/md-style-check.md` | CI markdown format validation rules |
| `zh-cn/contribute/markdown-check/API-reference-link-check.md` | API link anchor validation |
| `zh-cn/contribute/style-guide/style-guide-overview.md` | Style guide entry point |
| `zh-cn/contribute/style-guide/style-guide-example-code-style.md` | Example code formatting & `console.log` rule |
| `zh-cn/contribute/style-guide/style-guide-content-elements.md` | Tables, lists, admonitions, links rules |
| `zh-cn/contribute/template/` | Doc templates (guide, tutorial, FAQ, ts, native, js, etc.) |
| `.config/Profiles.json` | Branch-to-SDK-version mapping |
| `CODEOWNERS` | Per-file owner mapping |
| `skill/glossary_skill.md` | Glossary extraction skill |
| `skill/SKILL_common.md` | Batch-fix from detection results skill |
