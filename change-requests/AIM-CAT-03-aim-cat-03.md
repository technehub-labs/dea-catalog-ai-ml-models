# AIM-CAT-03: AIMLModel Candidate Corpus

**Status**: Landed (this PR)
**Layer**: Catalog content (candidate corpus intake)
**Owner**: Emmanuel A. Otchere
**Date**: 2026-11-15
**Admission authority**: candidate corpus only (canonical admission remains the evidence-gated step; FOUNDATIONS D-4/D-5)
**Trigger**: Catalog population programme (2026-11 owner directive): advance 10 foundational skeleton catalogs with evidence-backed candidate corpora (>=1,000 each) through a gated intake workflow. Ai-ml-models is seventh: the Hugging Face public model registry (top-1,500 by downloads) is the candidate seed source named per FOUNDATIONS §7. No AIMLModel-specific operational fields are asserted at candidate state (the metamodel schema is pending; the kit carries a derived projection).
**Carrier**: Single PR on feature branch `feat/aim-cat-03`. PR review, not direct push.
**Lands against**: `main`
**Depends on**: AIM-CAT-02 (ingestion groundwork).

## 1. What this CR lands

**1000 AIMLModel candidate submissions** in `contributions/queue/<shard>/<slug>.yaml` from 1 evidence bank(s):

| Bank | Source | Records |
|---|---|---|
| hf-models.json | Hugging Face public model registry (api/models by downloads) | 1000 |

Provenance in `ingestion/manifest.yaml` (bank sha256s, source URLs, retrieval dates, mapping note). Every submission carries `source_ref`, a `published-document` evidence citation, and published description prose. Provisional field mappings are documented per record and in the manifest; per-organization values are canonical-admission decisions.

> Provenance note: the AIMLModel metamodel schema is pending (schema-backfill named as follow-up CR material since the kit landed); records validate against the kit's derived std5 projection. Named follow-up: metamodel schema-backfill CR for dea:AIMLModel.

## 2. What changes

- `contributions/queue/<shard>/` — 1000 intake submissions (`status: queued`)
- `ingestion/manifest.yaml` — corpus provenance record (new)
- No `CATALOG.yaml` change (queue ≠ index)
- This CR file and the index row

## 3. Verification

- `check_contributions.py`: CONFORMANT (1000 queue files)
- No directory holds 800+ entries (slug-prefix distribution)
- Spot-checks: records trace to their published source identifiers

## 4. NOT-List

- NOT record admission (nothing under `entities/` changes; admission follows in AIM-CAT-04+).
- NOT a modification of gates, schemas, or intake tooling.
- NOT an authoritative assessment of provisional mapped values.

## 5. Acceptance criteria

1. 1000 gate-CONFORMANT submissions; manifest carries bank sha256s + source URLs.
2. Submissions carry no `id`; `status: queued`; `submitted_by: Emmanuel A. Otchere`.
3. `CATALOG.yaml` counts unchanged.
