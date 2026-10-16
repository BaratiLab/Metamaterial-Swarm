# Metamaterial Swarm

Physics-guided multi-agent selection of heterogeneous metamaterial unit cells, with beam and mechanical-cloaking experiments and numerical-search comparators.

## Source and reproducibility

Download and extract **Metamaterial-Swarm-source-and-results.zip**. It preserves the original directory structure, all project-authored Python and MATLAB code, committed agent actions, numerical outcomes, figures, and LaTeX manuscript source. `MANIFEST.json` lists every archived file and its SHA-256 checksum. Python source was checked for syntax before upload. Installed third-party runtimes and large solver caches are excluded.

| Extracted directory | Contents |
| --- | --- |
| `outputs/metamaterial-selector/` | Beam benchmark, numerical selectors, swarm actions, public library data, validation, and results |
| `outputs/cloak-experiment/` | Full-resolution cloak FEM port, adaptive selector, action replay, all 18 candidate assessments, retained assignments, and plots |
| `outputs/cloak-review/` | Supplied-package adapter, audit, and MATLAB wrapper |
| `outputs/overleaf-metamaterial-selector/` | LaTeX manuscript and supporting beam results |
| `outputs/agent-figures/` | Conceptual figures and visual checks |
| `work/` | Project-authored figure-generation, manuscript-generation, validation, and exploratory scripts; historical utilities may contain original-machine paths |

Begin with `outputs/metamaterial-selector/README.md`, `outputs/cloak-experiment/REPRODUCE.txt`, and `outputs/cloak-experiment/RESULTS.txt`. Install each experiment's `requirements.txt` in its own environment. Preserve the archived records; use a fresh output directory for replay.

### Replaying the cloaking experiment

The original `Agent_Meta` input package supplied by Liwei Wang must be provided separately. It is not redistributed here. From the extracted `outputs/cloak-experiment/` directory:

```bash
OPENBLAS_NUM_THREADS=1 OMP_NUM_THREADS=1 python replay_actions.py \
  --package /absolute/path/Agent_Meta --out /absolute/path/new-replay
```

Use Python 3.11 and the pinned dependencies. This replays the archived literal proposals without requiring new LLM decisions. The replay entry point was supplied after the experiment and has not itself been rerun through all 18 assessments. Numerical validation and the original assessments are recorded separately. Set `CLOAK_PACKAGE_DIR` and `CLOAK_WORK_DIR` when using `experiment.py` on another machine.

## Measured cloaking results

| Method | Displacement loss | Relative reduction from supplied assignment |
| --- | ---: | ---: |
| Supplied assignment | 12.7610% | — |
| Adaptive numerical search | 12.3594% | 3.15% |
| Three-agent swarm | 12.5406% | 1.73% |

Each search received nine distinct full-resolution candidate evaluations over three rounds, starting from the same supplied assignment. Evaluation retains the original 1500 × 1500 pixel discretization using exact mirror symmetry. The reference displacement comparison has relative monitored error about 1.3e-10. This is a Python port, not a MATLAB execution or a match to an author-reported scalar loss.

This is one exploratory case. The numerical policy was refined during the session; neither a preregistered comparison nor a statistical superiority claim is warranted. Both arms used a shared homogenized approximate model for proposal guidance. Full-resolution FEM determines acceptance. LLM decision records are archived, but model snapshot and decoding settings were not fully recorded. The manuscript currently covers the earlier beam study; it has not yet been updated with the cloaking results.

## Proposed next experiment

Improved coordination would combine a numerical optimizer, response and interface specialists, a shared measured experiment log, duplicate suppression, and FEM-based retention. A comparison against numerical search alone at 30 new FEM evaluations per method is proposed. **That coordinated experiment has not been run.**

## Attribution and redistribution

The beam library is from Liwei Wang et al., *2D orthotropic metamaterial micorstructrue dataset*, Figshare, [doi:10.6084/m9.figshare.17141975.v1](https://doi.org/10.6084/m9.figshare.17141975.v1), CC BY 4.0. Its original metadata and checksum records are retained under `outputs/metamaterial-selector/data/`.

Related paper: Wang et al., *Deep generative modeling for mechanistic-based learning and design of metamaterial systems*, CMAME 372 (2020), 113377, [doi:10.1016/j.cma.2020.113377](https://doi.org/10.1016/j.cma.2020.113377). The beam study is paper-inspired and does not reproduce every setting in that paper. The private author-supplied cloaking input package and correspondence are excluded. No new blanket software license is assigned by this research snapshot.
