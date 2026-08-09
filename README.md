# Ontogeny of a Workspace
This projects studies the ontogeny of global workspace representations during language-model pretraining such as when globally reusable conceptual representations emerge, whether their emergence follows some developmental transition, and what training dynamics cause models to merge distributed computations into a shared workspace. Currently we have a singular-learning-theoretic account of this transition, preliminary transformer experiments, and developmental results across Pythia checkpoints.

## Current status

**Confirmed, so far:**
- A free-energy theory (singular learning theory) of why broadcast beats redundant computation: Δλ = ½(K−1)r(d−r), verified to 1.3% in a closed-form linear model family, plus a three-axis (K, r, d) numerical sweep.
- Workspace steerability is a reproducible developmental event in Pythia: onset at step 767±66 (CV 9%, five 160M seeds), co-located with a fitted knee in the local learning coefficient (λ̂).
- A same-task, ablation-certified control confirms the free-energy preference directly in transformers (gaps +73/+223 at K=2/4).
- Pre-onset behavior is genuinely content-invariant, not merely a weak-probe artifact (natural-interchange control).
- The readable/steerable decoupling reappears in reverse after ablation and regrowth.

## Experiment map

**Completed**
- Pythia developmental sweep
- Linear-model gap law
- Transformer certified control
- Natural-interchange control
- Ablation and regrowth

**TODO**
- OLMo-2-1B developmental replication
- Kimi-K2 developmental replication
- Width-held-constant K-scaling control
- Matched-gradient dilution intervention
- Legibility-penalty intervention
- Precision and theory cleanup
- Checkpoint-localized intervention
- Data-dilution control
- Consumer-addition test
- Workspace competition experiment
- Rank-scaling test
- Causal mediation test
- Cross-scale onset law
- Persistence and hysteresis test

see `COMPUTE_BUDGET.md`: replicating the developmental study on OLMo-2-1B (the only public model family with a full pretraining checkpoint trajectory at this scale), a width-held-constant scaling control, and two designed training interventions (matched-gradient dilution, legibility-penalty training).

## Known caveats
Everything to date is at ≤410M parameters (Pythia) plus small synthetic transformers; no frontier-scale or second-model-family replication yet. Several theory results are order-of-magnitude-consistent rather than closed-form-exact (flagged explicitly in `theory/`). 
