# Parkinson EEG + control group

## Dataset Structure

The local dataset documentation describes:
  - `49` controls
  - `100` Parkinson disease subjects


! Data is already preprocessed, but for your information, we describe which preprocessing steps were performed.

## Preprocessing Pipeline

1. Load BrainVision `.vhdr` data with `mne.io.read_raw_brainvision`.
2. Set standard montage
3. Band-pass filter from `0.5 Hz` to `90 Hz`.
4. Apply `50 Hz` notch filter.
5. Apply average EEG reference with `set_eeg_reference("average")`.
6. Downsample to `125 Hz`.
7. Fit ICA and run automatic EOG component detection with `ica.find_bads_eog`. Fp1` was used for automatic EOG component detection.
8. Apply detected ICA exclusions.
9. Export as MNE raw FIF files named `*_preproc_raw.fif`.

