# SUEWS Hackathon Practice Setup

This is a practice repository for the SUEWS Community Hackathon setup check.

## Setup Status

| Step | Status |
| --- | --- |
| Repository created from template | Done |
| Task brief read | Done |
| suews-agent installed | Done |
| Demo SUEWS simulation run | Done |
| GitHub Pages enabled from `/docs` | Done |

## Smoke-Test Run

The setup check used the `suews@suews` Codex plugin and the SUEWS CLI it bootstraps through `uvx`.

- Latest case directory: `analysis/suews-agent-smoke-20260609-1418/`
- Config used for the latest run: `analysis/suews-agent-smoke-20260609-1418/updated_sample_config.yml`
- Output file: `analysis/suews-agent-smoke-20260609-1418/Output/KCL1_2012_SUEWS_60.txt`
- Evidence report: `analysis/suews-agent-smoke-20260609-1418/SMOKE_TEST_REPORT.md`
- SUEWS/SuPy version: `2026.6.5`
- Schema version: `2026.5`

This was a Level 1 demo run using the packaged KCL/London sample data. It confirms the local toolchain can initialise, validate, run, diagnose, and summarise a SUEWS case end to end. It should not be interpreted as the hackathon city result.

## Honest Caveats

Validation completed with warnings only, mostly about unused zero-fraction surfaces and albedo/emissivity consistency checks in the sample setup. Post-run diagnostics found the output file and no NaNs in QH/QE/QN, but flagged an energy-balance closure warning for this demo output.

The on-the-day hackathon submission still needs the released focus-city dataset, the heat-to-risk bridge function, and a proper interpretation of hazard and socio-economic risk.
