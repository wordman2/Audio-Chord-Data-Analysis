# Musical Instrument Chord Analysis

This project analyzes audio recordings of musical chords (major and minor) played on piano and guitar. The analysis involves pre-processing the audio data, extracting features, and visualizing patterns using techniques like Fast Fourier Transform (FFT) and spectrograms.

---

## Dataset

The dataset contains piano and guitar recordings of chords, labeled as either major or minor. The recordings were scraped from various sources and are freely available on [Kaggle](https://www.kaggle.com/datasets/deepcontractor/musical-instrument-chord-classification/data).

---

## Features Extracted

1. **Channel Type**: Mono or Stereo.
2. **Sample Rate**: 44,100 Hz.
3. **Bit Depth**: 16-bit.
4. **Root Mean Square (RMS)**: Calculated for both original and trimmed signals.
5. **Duration**: Length of the trimmed audio signals.

---

## Pre-Processing

1. **Loading Audio**: Audio files are loaded using `librosa`, preserving their native sample rate and stereo/mono configuration.
2. **Trimming Silence**: Silence at the start and end of recordings is removed using `librosa.effects.trim`.
3. **Feature Extraction**: RMS and duration are calculated for trimmed signals.

---

## Analysis and Visualization

### 1. **Fast Fourier Transform (FFT)**
- Converts audio signals from the time domain to the frequency domain.
- Peaks in the frequency spectrum are identified to detect harmonics.
- Frequencies are mapped to musical notes using the `music21` library.

### 2. **Spectrograms**
- Visualizes the frequency spectrum over time.
- Highlights differences between piano and guitar recordings:
  - Guitar recordings have more overtones and a broader upper frequency spectrum.
  - Piano recordings are more present in the lower frequency range (< 250 Hz).

---

## Results

1. **Chord Detection**:
   - Major chords like C major were detected with some inaccuracies (e.g., missing lower notes or detecting extra notes like B4).
   - Complex chords (e.g., 9th and 6th chords) were harder to detect due to disharmonic sounds.

2. **Instrument Comparison**:
   - Guitar recordings exhibit a richer overtone structure.
   - Piano recordings emphasize lower frequencies.

---

## How to Run

1. Install dependencies using the provided `environment.yml` file:
   ```bash
   conda env create -f environment.yml
   conda activate CA2_WWD