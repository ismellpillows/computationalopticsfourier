# Computational Optics from Audio Fourier Fields

This project transforms music clips into optics-inspired images and evaluates whether those images can support music genre recognition.

## Final pipeline

The final notebook uses:

- the GTZAN dataset,
- 5-second windows with 2.5-second hop,
- mel-scaled frequency organization,
- a strong baseline based on mel spectrogram images,
- optics-derived image variants built from the same windows,
- a three-channel mel-optics representation containing magnitude, phase, and propagated intensity,
- dataset-level standardization,
- mild geometric augmentation, and
- a compact residual CNN.

## Main result

The final selected system is:

- **representation:** `mel_optics_multichannel`
- **model:** `residual_cnn`

In the executed comparison run recorded by the project summary, this design outperformed the mel spectrogram baseline and reached approximately:

- **final test accuracy:** 0.803
- **final macro F1:** 0.808

## Files

- `audio_optics_genre_research.ipynb` — final research notebook
- `sample.ipynb` — original exploratory notebook kept for reference
- `DEV.md` — developer notes and implementation record
- `requirements.txt` — Python dependencies
- `outputs/run_summary.json` — final run summary and metrics

## Running the project

Use the workspace virtual environment and run the notebook from top to bottom. The notebook includes dataset download code and writes summary outputs automatically.

## Notes

- GTZAN contains one unreadable file in the downloaded archive in some environments; the notebook is written to skip corrupt items safely.
- The final comparison stage uses balanced window sampling to stay within practical memory limits while preserving a fair representation comparison.
