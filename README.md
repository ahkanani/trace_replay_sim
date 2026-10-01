# Trace Replay Sim

An independent simulator for replaying MoE expert-routing traces and comparing
GPU, PIM, and remote-memory placement and scheduling policies. It builds
TracePacks from raw routing traces, simulates continuous batches, and produces
metrics and reports. It does not require LLMServingSim or ASTRA-Sim.

## Install

Requires Python 3.10 or newer. From this repository:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -e .
pim-hot-cold-moe --help
```

## Workflows

```bash
pim-hot-cold-moe trace build --config /path/to/trace-build.yaml
pim-hot-cold-moe trace inspect --trace-pack /path/to/pack
pim-hot-cold-moe simulate --config configs/experiments/standard_smoke/qwen3_235b_a22b_fp8_mmlu_smoke.yaml
pim-hot-cold-moe report --run /path/to/run
```

The supplied experiment configs require external TracePacks at their configured
paths. Model and hardware definitions live under `configs/models/` and
`configs/hardware/`; sweep scripts live under `scripts/`.

## Provenance

Extracted from `trace_replay_sim/` on LLMServingSim's `bd-opensource-release`
branch using `git subtree split`. Commit `443f8f7` preserves the source subtree
and the original import's author, date, and message. The extraction does not
recover earlier development commits that were absent from the published branch.
The subsequent commit adds only this README, ignore rules, and the parent
project's inherited MIT license.

The repository is published at https://github.com/ahkanani/trace_replay_sim
on branch `codex/trace-replay-extracted`.
