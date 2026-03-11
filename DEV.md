# Development Journal

## Goal
Build a reproducible research notebook that transforms audio into optics-inspired images, compares multiple representation choices fairly, and reports a final genre-classification result.

## Final technical decisions
- Use GTZAN as the labeled benchmark dataset.
- Expand tracks into 5-second windows with 2.5-second hop to produce a much larger supervised dataset.
- Use mel-scaled frequency organization for both the baseline and optics-aligned transforms.
- Compare four image representations: mel spectrogram, mel Cartesian optics, mel radial optics, and a multi-channel mel optics image.
- Use group-aware splitting by original track path so windows from the same song do not leak across train, validation, and test sets.
- Standardize images using statistics from the training split only.
- Use mild translation and zoom augmentation only.
- Compare a small CNN and a compact residual CNN, then retrain the selected winner.

## Important implementation notes
- The strongest representation was the multi-channel mel optics image containing magnitude, wrapped phase, and propagated intensity.
- The strongest model was the compact residual CNN.
- The old handcrafted-feature pipeline and earlier full-song image-only experiments were superseded by the final ablation-driven notebook design.
- GTZAN can include corrupt files or metadata artifacts; the notebook filters and skips bad items safely.
- Half-precision caching was used for the rendered comparison dataset to keep memory use manageable.

## Reproducibility tips
- Use the workspace virtual environment at `.venv`.
- Run the notebook from top to bottom.
- The notebook downloads GTZAN automatically if needed.
- Final metrics are written to `outputs/run_summary.json`.
