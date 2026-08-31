SAGE-VAD REPRODUCIBILITY BUNDLE


Purpose
-------
This bundle supports 
"SAGE-VAD: SNR-Adaptive Gated Enhancement with Lightweight Spectro-Temporal Attention for Robust Speech Activity Detection in Noisy Environments".

IMPORTANT SCIENTIFIC SCOPE
--------------------------
1. SynNoisyVAD is a PROGRAMMATICALLY GENERATED SYNTHETIC benchmark. It does not contain human recordings.
2. The numerical results in the manuscript were obtained by running the included synthetic-data experiment, not copied from NOIZEUS or another public corpus.
3. The generated benchmark is designed to test controlled SNR/noise behavior and method mechanics, not to establish clinical or deployment-level generalization.

Dataset summary
---------------
- 840 clips, 2.4 s each, 8 kHz
- 720 clips from six seen noise families: babble, car, street, restaurant, airport, exhibition
- 120 clips from held-out construction noise
- SNR: -10, -5, 0, 5, 10, 15 dB
- 20 replicates per noise-by-SNR cell
- 200,760 total analysis frames
- 13 acoustic features from noisy and enhanced views
- clip-level train/validation/test split for seen noise: 504/108/108 clips

Key files
---------
data/SynNoisyVAD_metadata.csv   clip metadata
data/SynNoisyVAD_features.npz   generated frame features/labels
data/splits.json                clip-level split identifiers
sample_dataset_rows.csv         sample frame-level rows used in manuscript
run_experiment.py               primary generator/training experiment
refine_full.py                  refined full SAGE-VAD training
refine_ablation.py              matched ablation runs
make_figures.py                 manuscript graph generation
fair_main_results.csv           paired held-out baseline/full-model metrics
per_snr_model_metrics.csv       F1 by SNR and model
refined_detailed_seen_metrics.csv noise-family metrics
refined_full.json               full model metrics/configuration
refined_ablation_A.json         ablations A
refined_ablation_B.json         ablations B
significance.json               bootstrap and McNemar analysis
figures/                        manuscript figures

Headline synthetic test results
-------------------------------
SAGE-VAD: accuracy 93.63%, precision 92.31%, recall 97.63%, F1 94.89%, AUROC 98.54%.
At -10 dB: F1 88.49% versus 81.31% logistic regression and 70.77% energy threshold.
McNemar paired comparison vs logistic regression: chi-square 277.73, p ≈ 2.35e-62.
Ablation F1 decrease vs full model: no SNR auxiliary -0.50 pp; no enhancement -0.54 pp; fixed fusion -0.75 pp; no Transformer -2.95 pp.

Reproducibility note
--------------------
The manuscript reports a single fixed seed (20260815). 
