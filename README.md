# Evidence-Aware Compositional Runtime Verification for LLM-Assisted ISR Swarms

**Authors.** Nikolaos Kekatos, Theodoros Nestoridis, Michael Ioannou, Panagiotis Katsaros,
Alexios Lekidis, Tom Nianios, Dimitrios Nikou. Submitted to **MESAS 2026**.

Verdicts carry a security value *and* an evidence-completeness value, so evidence an adversary jams
or drops becomes an explicit `unknown` rather than a swarm-wide all-clear. Over live brokers the
protocol commits zero silent false all-clears where a best-effort central monitor commits three.

## Layout

```
paper/     submitted manuscript and source
code/      monitors, mission generator, fault injection, experiment drivers
  ros2_realism/    the same monitors over ROS 2 / DDS
  sitl_mission/    ArduPilot SITL mission over MAVLink
results/   recorded outputs, including the archived LLM calls
```

## Running

Stdlib only for the deterministic suites.

```sh
cd code
python3 run_demo.py           # attack and benign missions, L1 vs L3 verdicts
python3 experiments.py        # four objectives x three faults
python3 exp_baselines.py --md  # stronger baselines and complementary metrics
```

Live brokers, ROS 2 and SITL each need their own stack; see the scripts' docstrings.

## What reproduces

Deterministic suites use fixed seeds and reproduce exactly. The scale timings are wall-clock and
vary between runs. Archived LLM outputs are preserved rather than regenerable, since hosted models
change.
