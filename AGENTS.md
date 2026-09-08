# AGENTS.md

Guidance for AI agents working in the OpenHarmony **docs** repository.

## What this repo is

- **Docs-only repo.** Content is Markdown + images. There is **no build, test, lint, or typecheck** command to run here.
- `docker/`, `point.md`, and `en/device-dev/subsystems/subsys-build-*.md` describe building the OpenHarmony **OS** in *other* repos — do not run those commands here or assume they verify this repo.
- Hosted on GitCode (`gitcode.com/openharmony/docs`), not GitHub. PR/issue templates live in `.gitcode/`.

## Bilingual structure (critical)

- Two parallel content trees: **`zh-cn/`** (Chinese, source of truth) and **`en/`** (English, translated). They mirror each other directory-for-directory.
- Per `en/contribute/writing-instructions.md`: Chinese is preferred and leads; English is produced by translation after Chinese is reviewed. When making a change, edit `zh-cn/` first and keep `en/` in sync unless told otherwise.
- `zh-cn/` READMEs are newer — `README_zh.md` lists versions up to 6.1 (API 23) while `README.md` tops out at 6.0 (API 20). Trust `zh-cn` when they diverge.

## Directory layout (mirrored under `zh-cn/` and `en/`)

- `application-dev/` — app-dev docs, organized by Kit/subsystem (e.g. `ui/`, `media/`, `security/`, `application-models/`). Navigation in `application-dev/Readme-EN.md`.
- `application-dev/reference/` — API references (TS/JS/native), the largest and most churn-heavy area.
- `device-dev/` — device/porting/kernel/driver docs.
- `release-notes/` — per-version release notes.
- `contribute/` — contribution guides, writing specs, coding style guides, and **templates** (see below).
- `design/`, `figures/`, `glossary.md`, `Legal-Notices.md`.

## Doc authoring conventions

- **File names**: kebab-case `.md`, e.g. `write-standard.md`. No spaces.
- **Images**: place in a `figures/` folder **next to** the referencing doc; reference with relative paths (markdown image syntax pointing to `figures/xxx.png`). Recommended: `.png`, ≤150 KB, ~640 px tall, ≤820 px wide. Text on images must match the doc's language.
- **Tables**: every table needs a caption and a header; use `_` for empty cells, never leave blank.
- **Start from a template.** `en/contribute/template/` holds required structures: `readme-template.md`, `ts-template.md`, `js-template.md`, `native-template.md`, `guide-template.md`, `faq-template.md`, `tutorial-template.md`, `errorcodes-template.md`. Match the template's section order.
- **Navigation `Readme-EN.md` / `Readme-EN.md` files are TOCs.** When adding/renaming/deleting a `.md` page, update the relevant `Readme-EN.md` so links stay valid, and check for inbound links from other docs.
- **Readme files carry HTML-comment metadata** that downstream tooling reads — preserve and update it:
  ```text
  <!--Kit: Common-->
  <!--Subsystem: Common-->
  <!--Owner: @username-->
  <!--Designer: @username-->
  <!--Tester: @username-->
  ```

## API reference rules (from `ts-template.md` / `js-template.md`)

- One reference doc per `.d.ts` file; named `ts-<class>-<name>.md`. Upload to `docs/en/application-dev/reference/apis-<Kit>-kit/`.
- Map `.d.ts` tags to doc fields: `@since`, `@deprecated`, `@systemapi`, `@syscap`, `@permission`, `@form`, `@FAModelOnly`/`@StageModelOnly`, `@extends`.
- Mark version with superscript: `newMethod<sup>7+</sup>`. Don't delete deprecated APIs — annotate them and point to the replacement.
- API order in the doc must match code order.

## Branch & API-level mapping

- `master` = latest. Branch → SDK version pairs are defined in `.config/Profiles.json` (the executable source of truth): `master`→SDK 20, `OpenHarmony-5.1.0-Release`→SDK 18. `.config/*.xlsx` hold the API-consistency and sample-code-accuracy profiles/whitelists.
- Active release branches to consider for cherry-pick are listed in `.gitcode/PULL_REQUEST_TEMPLATE.zh-CN.md`. **Always ask/consider whether a change needs back-porting to active release branches** — this is a required field on the PR template.

## License (don't get this wrong)

- **Documentation content is licensed CC-BY-4.0** — declared in `OAT.xml` (`<policyitem type="license" name="CC-BY-4.0" path=".*" ...>`). The root `LICENSE` (Apache 2.0) covers repo scaffolding, not doc content.
- Do **not** add Apache 2.0 source-file headers to Markdown docs. `en/contribute/license-and-copyright-specifications.md` and `OAT.xml` are the references; `en/contribute/` is excluded from OAT scanning.

## Contribution workflow

- **DCO required.** Commit with `git commit -s` so `Signed-off-by` is added; the name/email must match your DCO. See `DCO.txt`.
- **PR template** (`.gitcode/PULL_REQUEST_TEMPLATE.zh-CN.md`) requires: change type (new/changed/VOD-fix/optimization), linked interface-repo `.d.ts` PR if API docs changed, a self-check checklist, and **screenshot proof that sample code compiles AND runs on a device** (compile log + run log; any error code, even non-blocking, counts as a failure). Also requires a **DocLinter** AI scan report link.
- **Two approvals to merge**: `TechApprove` (service SIG technical expert) **and** `DocsApprove` (Docs SIG expert). Use `@`-mentions per `en/contribute/docs-reviewers.md`.
- **CODEOWNERS is per-file and huge** (~5560 lines). To find the right reviewers for a file you're touching, search `CODEOWNERS` for the path — do not assume directory-level ownership.

## Git LFS

`.gitattributes` marks binary types (`.tgz`, `.zip`, `.jar`, `.so`, `.dll`, `.dylib`, `.bin`, `.mp4`, `.asm`, etc.) as LFS. `.png` images are **not** LFS. Ensure `git-lfs` is installed before cloning/pulling to avoid corrupted binary checkouts.
