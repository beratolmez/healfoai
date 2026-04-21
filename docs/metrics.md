# Model Metrics Snapshot

This file summarizes the currently observed ML baseline signals from the first Kaggle notebook runs.

## Detector Baseline

Model:

- `YOLOv8n`
- single detector class: `food`

Observed validation metrics:

- Precision: `0.947`
- Recall: `0.852`
- mAP50: `0.948`
- mAP50-95: `0.723`

Observed run context:

- `4702` validation images
- `4734` instances
- runtime note from notebook: ~`1.7ms` inference per image reported by the validation summary on Kaggle hardware

Interpretation:

- strong baseline for single-class food-region detection
- good enough to justify continued detector research
- not yet sufficient, by itself, for production rollout without the crop + classifier benchmark path

## Classifier Baseline

Model:

- `EfficientNet-B0`
- `36` classes in the observed notebook run

Observed results:

- Stage 1 best validation accuracy: about `0.526`
- Stage 2 best validation accuracy: about `0.831`
- late-stage training accuracy: about `0.964`

Interpretation:

- strong baseline for an early classifier run
- clear generalization gap between train and validation
- product-readiness still requires:
  - per-class evaluation
  - confusion analysis
  - test-set reporting
  - real-device / real-scene validation
  - unknown / low-quality handling checks

## Important Caveat

These metrics are useful research signals, not final product metrics.

The production decision path in the main project remains:

1. benchmark
2. shadow telemetry
3. gated rollout
4. only then runtime promotion
