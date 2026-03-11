# Computational Optics from Audio Fourier Fields

This project turns labeled audio clips into optics-inspired images and tests whether those images are useful for music genre classification.

## What is in this repo?

- `audio_optics_genre_research.ipynb` — the main research notebook
- `sample.ipynb` — older exploratory notebook provided as a reference
- `TestAudio2.mp3` — local sample audio for transform demos
- `DEV.md` — running developer journal and implementation notes
- `requirements.txt` — Python dependencies

## Project idea

The notebook treats the STFT of an audio signal as a complex field $E(t, f)$ over time and frequency. That allows us to borrow an optics interpretation:

1. compute a complex STFT from audio,
2. interpret the result as a wave field,
3. simulate optical measurement using a 2D Fourier transform,
4. form intensity $I = |\mathcal{F}_2(E)|^2$,
5. use the resulting images for machine learning.

The project compares three image representations:

- baseline spectrogram image,
- Cartesian optics intensity image,
- radial optics intensity image.

## Environment

A virtual environment is expected in `.venv`.

On Windows PowerShell, one workable setup is:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
python -m ipykernel install --user --name computionalopticsfourier
```

## How to use the notebook

Open `audio_optics_genre_research.ipynb` and run the cells from top to bottom.

The notebook supports two modes:

1. **Quick demo mode**
   - uses `TestAudio2.mp3`
   - does not require downloading the full dataset
   - validates the audio-to-image pipeline

2. **Dataset mode**
   - downloads GTZAN from code inside the notebook
   - extracts labeled audio clips
   - builds image-derived features
   - trains and evaluates genre classifiers

Inside the notebook, look for these toggles:

- `DOWNLOAD_GTzan`
- `RUN_FULL_DATASET`
- `MAX_PER_GENRE`

## Outputs

Generated artifacts are written under folders such as:

- `data/`
- `cache/`
- `outputs/`
- `figures/`
- `models/`

A small run summary is written to `outputs/run_summary.json`.

## Notes

- The full GTZAN download is large, so the first clean run may take a while.
- The notebook is intentionally designed around lightweight classical ML baselines for reproducibility.
- A natural extension is to add a compact CNN trained directly on the generated images.
