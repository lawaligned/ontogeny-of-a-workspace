# Compute budget

## Measured baselines (this project, to date)

- Pythia-70m: J-lens fit ≈2.1 s/prompt, 80-prompt fit ≈3 min/checkpoint (M4 Pro, MPS).
- Pythia-160m: ≈8.4 s/prompt, ≈11 min/checkpoint fit; λ̂ (3 SGLD chains × 150 draws) ≈7 min/checkpoint.
- Small transformer organism (K-consumer certified control, D=128, 2 layers): ≈2.5–3 min/organism training + λ̂ measurement on a rented A10.
- Full Tier-1 GPU battery (organism training + λ̂ across K=2,4,8, two seeds, broadcast+dedicated): **~2 hours, ~$2.60** total. This was sufficient for
- small-scale validation, but larger-scale replication requires significantly more compute.

OLMo-2-1B is roughly 6–14× the parameter count of anything lens-fit or λ̂-estimated to date; cost does not scale linearly with parameters for
either operation (lens fitting is dominated by backward passes per prompt; λ̂ estimation by SGLD chain length), so Tier 2's benchmark step exists
to replace the extrapolation below with a measured number before full spend.

Additional experiments not yet benchmarked include applying J-lens analysis to larger open-weight models such as OLMo-2-1B and Kimi K2,
investigating whether reasoning-related representations can be reverse-engineered in mathematical tasks, and extending interpretability
experiments to better understand the internal structures associated with capability and alignment-relevant behaviors.

## Dollar conversion

Approximate current A100/H100-class cloud rates (confirm at time of spend
— this project's only prior rental was a Lambda A10 at $1.29/GPU-hour,
which is not representative of A100/H100 pricing):

| GPU | Approx. rate |
|---|---|
| A100 80GB | $1.50–$2.50/GPU-hour |
| H100 80GB | $2.50–$4.50/GPU-hour |

At these rates, the replication and additional experiments are estimated at approximately 300–350 GPU-hours, corresponding to roughly $450–$875 on A100s or
$750–$1,575 on H100s depending on actual usage. The requested reserve is intentionally above the raw arithmetic to account for setup overhead, failed jobs,
idle time, and higher-than-estimated costs at 1B-scale.
