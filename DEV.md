# Development Journal

## Goal
Build a reproducible research notebook that transforms audio into optics-inspired images, trains genre classifiers on those images, and reports meaningful observations.

## Notes learned during implementation
- The existing sample notebook already sketches a spectrogram-to-image idea, but it normalizes per segment and drops phase information. For the optics framing, it is more useful to keep a complex STFT field so the notebook can treat the data as a wave field $E(t, f)$ before forming intensity images.
- GTZAN is a practical dataset choice for a classroom project because it is a standard genre benchmark with 1,000 labeled clips and can be downloaded from Python code.
- Fully materializing every transformed image can be slow, so the notebook should support a capped subset for faster demonstrations while still allowing a full run.
- A lightweight classical ML baseline on engineered image descriptors is more reliable in a fresh notebook environment than a heavier deep learning pipeline, especially on Python 3.13.
- Comparing representations is interesting: Cartesian optics intensity, radial optics intensity, and direct spectrogram-based image summaries may lead to different classification performance.

## Reproducibility tips
- Use the workspace virtual environment at `.venv`.
- The notebook includes data-download code so a clone can reproduce the pipeline.
- If dataset download is slow or unavailable, the notebook can still run the transformation demo on `TestAudio2.mp3`.
- Keep generated data under ignored folders such as `data/`, `outputs/`, and `artifacts/`.

## Future developer ideas
- Add caching of computed transforms as compressed arrays for faster reruns.
- Try a compact CNN once the environment is expanded to a deep learning stack.
- Compare optics-inspired transforms against mel spectrograms and CQT baselines.
