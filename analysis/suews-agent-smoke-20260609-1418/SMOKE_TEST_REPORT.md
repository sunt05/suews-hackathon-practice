# SUEWS Agent Smoke-Test Report

Date: 2026-06-09

## Outcome

Run status: completed
Readiness: Level 1 - demo

This was a small setup check using the `suews@suews` Codex plugin and the SUEWS CLI bootstrapped through `uvx`. The case uses the packaged KCL/London sample configuration and forcing data, so it proves the toolchain works but is not a site-specific or hackathon-city result.

## Commands Used

```bash
uvx --from 'git+https://github.com/UMEP-dev/SUEWS.git#subdirectory=mcp' suews init --template simple-urban --format json analysis/suews-agent-smoke-20260609-1418
uvx --from 'git+https://github.com/UMEP-dev/SUEWS.git#subdirectory=mcp' suews inspect --format json analysis/suews-agent-smoke-20260609-1418/sample_config.yml
uvx --from 'git+https://github.com/UMEP-dev/SUEWS.git#subdirectory=mcp' suews validate --format json analysis/suews-agent-smoke-20260609-1418/sample_config.yml
uvx --from 'git+https://github.com/UMEP-dev/SUEWS.git#subdirectory=mcp' suews run analysis/suews-agent-smoke-20260609-1418/updated_sample_config.yml
uvx --from 'git+https://github.com/UMEP-dev/SUEWS.git#subdirectory=mcp' suews diagnose --format json analysis/suews-agent-smoke-20260609-1418
uvx --from 'git+https://github.com/UMEP-dev/SUEWS.git#subdirectory=mcp' suews summarise --variables Tair,QH,QE,QN --format json analysis/suews-agent-smoke-20260609-1418/Output
```

## Evidence

- `suews init` reported status `success`.
- `suews inspect` reported site `KCL`, latitude `51.51`, longitude `-0.12`, and forcing file `Kc_2012_data_60.txt`.
- `suews validate` completed with status `warning`, no errors, and wrote `updated_sample_config.yml`.
- `suews run` completed with `SUEWS run successfully done!`.
- `suews diagnose` found one output file and reported NaN fractions of `0.0` for QH, QE, and QN.
- `suews summarise` reported 8784 output steps.

## Key Summary Values

| Variable | Mean | Min | Max | NaN percent |
| --- | ---: | ---: | ---: | ---: |
| QH | 88.7596 | -40.8153 | 339.7017 | 0.0 |
| QE | 27.5850 | 1.6983 | 195.3424 | 0.0 |
| QN | 44.7600 | -83.7954 | 646.9792 | 0.0 |

`Tair` was requested in the summary command but is not present in the SUEWS output file under that name.

## Caveats

- This is the packaged KCL/London sample case, not the hackathon focus city.
- Validation warnings remain for unused zero-fraction surfaces and sample albedo/emissivity consistency checks.
- Diagnostics flagged a mean energy-balance closure residual of `5.731`; this should be reviewed for any scientific use.
- The CLI run did not automatically emit a provenance sidecar, so `provenance.json` was added manually from the command outputs.

## Interpretation Boundary

This run confirms the setup works end to end: initialise, inspect, validate, run, diagnose, and summarise. It is suitable as a setup smoke test only.
