---
name: cdisc-resolve-variable-terminology
description: >-
  Resolve an SDTM variable to the CDISC Controlled Terminology codelist that governs its values, so a dataset
  value can be checked against the submission values CDISC publishes.
api: CDISC Library API
base_url: https://library.cdisc.org/api
auth: api-key header
operations:
  - listSdtmVersions
  - getSdtmDataset
  - listTerminologyPackages
  - listCodelists
generated: '2026-09-17'
method: generated
source: openapi/cdisc-sdtm-api-openapi.yml, openapi/cdisc-terminology-api-openapi.yml
---

# Resolve an SDTM variable to its controlled terminology

Use this when you have a dataset (domain) and a variable — say `AE.AESEV` — and need the authoritative list of
values CDISC allows for it.

## Before you start

- Every call needs the `api-key` header. Keys come from https://api.developer.library.cdisc.org/ after a CDISC
  Library account is approved. Without it the gateway returns
  `401 { "statusCode": 401, "message": "Access denied due to missing subscription key..." }`.
- Everything here is a GET. There is nothing to undo and no idempotency key to send.

## Steps

1. **Pick the standard version.** `GET /mdr/sdtm` (`listSdtmVersions`) returns the published SDTM versions.
   Versions are hyphenated, not dotted — `1-4`, not `1.4`. Pin one; published versions never change.
2. **Get the dataset.** `GET /mdr/sdtm/{version}/datasets/{dataset}` (`getSdtmDataset`) returns the domain with
   its `variables[]`. If you do not know the domain name, list them first with
   `GET /mdr/sdtm/{version}/datasets` (`listSdtmDatasets`), or list the classes with
   `GET /mdr/sdtm/{version}/classes` (`listSdtmClasses`) when you are navigating by Events / Interventions /
   Findings / Special Purpose.
3. **Read the codelist binding.** On the variable object, `codelistSubmissionValues` carries the codelist
   submission value(s) that govern it. `role` and `core` tell you how the variable is used and whether it is
   Required / Expected / Permissible. An empty `codelistSubmissionValues` means the variable is not
   terminology-controlled — that is an answer, not a miss.
4. **Choose a terminology package.** `GET /mdr/ct` (`listTerminologyPackages`) returns CT packages by release
   date. CT is versioned separately from SDTM, so you must choose the package date your study uses.
5. **Pull the codelist.** `GET /mdr/ct/{packageDate}/codelists` (`listCodelists`) returns the codelists in that
   package; match on the submission value from step 3 and read its terms.

## Handling failures

- `404` — the version, dataset or package date does not exist. Re-list the parent collection and use the
  identifier it returns; never construct one.
- `403` — the key is valid but not entitled to that product. Entitlement is by CDISC membership.
- `500 / 503 / 504` — retry with backoff and check https://cdisc.statuspage.io for an open incident.

## Notes

- Responses are linked data: follow `_links` / `_embedded` rather than guessing child paths.
- Ask for the representation you want with `Accept` — JSON, XML, ODM-XML, CSV and Excel are all supported.
- No pagination exists on these collections; they return in full.
