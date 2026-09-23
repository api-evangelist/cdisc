---
name: cdisc-validate-with-core
description: >-
  Validate a study dataset against published CDISC conformance rules using CORE, CDISC's open-source rules
  engine, backed by rules and standards metadata pulled from the CDISC Library API.
api: CDISC CORE (Checks and Rules Engine)
tool: cdisc-rules-engine
auth: api-key header (CDISC Library), supplied to the engine
operations: []
generated: '2026-09-17'
method: generated
source: >-
  https://github.com/cdisc-org/cdisc-rules-engine/blob/main/docs/cli-reference.md , cli/cdisc-cli.yml,
  packages/cdisc-packages.yml
---

# Validate a dataset with CDISC CORE

CORE is a command-line tool, not an API. There is no hosted CDISC validation endpoint — the conformance rules
live in the CDISC Library and the engine runs on your machine against your data, which is why study data never
leaves it.

## Install

Any one of:

- `pip install cdisc-rules-engine` (PyPI, 0.17.1 as of 2026-08-31)
- the pre-built executable from the GitHub releases page — `./core` (Linux/macOS), `.\core.exe` (Windows)
- `docker pull cdiscdocker/cdisc-rules-engine`
- from source: `python core.py`

## Steps

1. **Cache the rules and standards.** Run `update-cache`. This is the step that calls the CDISC Library API, so
   it is where your `api-key` is needed. Everything after it works offline against the cache.
2. **Validate.** `python core.py validate -s <standard> -v <version> -d <data-directory>`
   - `-s, --standard` — e.g. `sdtmig`, `tig`
   - `-v, --version` — e.g. `3-4`
   - `-ss, --substandard` — required for TIG: one of `SDTM`, `SEND`, `ADaM`, `CDASH`
   - `-dxp, --define-xml-path` — pass the Define-XML; with Define-XML 2.1 the controlled terminology is taken
     from the define and you do not need `-ct`
   - `-ct, --controlled-terminology-package` — otherwise name the CT package(s) explicitly
3. **Scope the run if you need to.** `-r/--rules` runs only named CORE rule IDs (e.g. `CORE-000001`),
   `-er/--exclude-rules` skips them, `-lr/--local-rules` loads rules you wrote yourself.
4. **Choose an output.** `-o` sets the path (no extension — the engine adds it) and
   `-of/--output-format` takes `JSON`, `XLSX` or `CSV`. CSV writes issue rows directly
   (Dataset, Record, Variable, Value).
5. **Read the statuses.** Every rule reports one of `SUCCESS`, `SKIPPED`, `ISSUE REPORTED` or
   `EXECUTION ERROR`. `SKIPPED` is not a pass — the rule could not run because a column or domain was absent,
   or it was out of scope.

## Notes

- External dictionaries are supplied as paths or URLs, not bundled: `--whodrug`, `--meddra`, `--loinc`,
  `--medrt`, `--unii`, and `--snomed-url` / `--snomed-version` / `--snomed-edition`.
- `-ps/--pool-size` parallelises; large datasets are processed with Dask.
- Most flags have environment-variable equivalents (`PRODUCT`, `VERSION`, `SUBSTANDARD`, `CT`, `DEFINE_XML`,
  `MAX_REPORT_ROWS`), which is what you want in CI.
