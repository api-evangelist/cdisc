---
name: cdisc-read-analysis-results
description: >-
  Walk a CDISC Analysis Results Standard (ARS) reporting event — its planned analyses, methods, operations,
  outputs and displays — from the CDISC Library API.
api: CDISC Library API (Analysis Results Standard)
base_url: https://library.cdisc.org/api
auth: api-key header
operations:
  - api.products.ars.get_packages
  - api.products.ars.get_package_reportingevents
  - api.products.ars.get_package_reportingevent
  - api.products.ars.get_package_reportingevent_analysis
  - api.products.ars.get_package_reportingevent_method
  - api.products.ars.get_package_reportingevent_method_operation
  - api.products.ars.get_package_reportingevent_output
  - api.products.ars.get_package_reportingevent_output_display
generated: '2026-09-17'
method: generated
source: openapi/cdisc-ars-api-openapi.yml
---

# Read an ARS reporting event

The Analysis Results Standard describes what a study PLANS to analyse and report — the analyses, the
statistical methods behind them, and the outputs and displays they land in. All 17 operations are reads.

## Steps

1. **List packages.** `GET /mdr/ars/packages` (`api.products.ars.get_packages`).
2. **List reporting events in a package.** `GET /mdr/ars/packages/{package}/reportingevents`
   (`api.products.ars.get_package_reportingevents`).
3. **Get the reporting event.** `GET /mdr/ars/packages/{package}/reportingevents/{reportingevent}`
   (`api.products.ars.get_package_reportingevent`). This is the root object; everything below hangs off it and
   is reachable through its `_links`.
4. **Follow the branch you need** — each is a separate operation under the reporting event:
   - analyses: `.../analyses/{analysis}` and `.../analyses/{analysis}/datagroupings/{datagrouping}` and
     `.../datagroups/{datagroup}`
   - methods: `.../methods/{method}`, `.../methods/{method}/operations/{operation}`, and
     `.../operations/{operation}/refoprels/{refoprel}`
   - outputs: `.../outputs/{output}` and `.../outputs/{output}/displays/{display}`
   - population and subsetting: `.../analysissets/{analysisset}`, `.../datasubsets/{datasubset}`,
     `.../analysisgroupings/{analysisgrouping}` and `.../analysisgroupings/{analysisgrouping}/analysisgroups/{analysisgroup}`
   - categorization: `.../categorizations/{categorization}` and `.../categorizations/{categorization}/categories/{category}`

## Handling failures

The ARS contract declares the full set: `400`, `401`, `403`, `404`, `405`, `406`, `500`, `503`, `504`. The body
is `{ "statusCode", "message" }` — there is no RFC 9457 problem document and no stable error code, so branch on
the status, not the message. `406` means the representation you asked for in `Accept` is not available for that
resource.

## Notes

- Take identifiers from the parent response rather than composing paths by hand — the child segments are names,
  not opaque ids, and a guessed one returns `404`.
- Nothing here mutates; a retry is always safe.
