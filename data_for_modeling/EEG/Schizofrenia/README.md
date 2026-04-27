# Schizophrenia EEG Dataset


- `norm/`: healthy control recordings
- `sch/`: schizophrenia recordings

! Data is already preprocessed, but for your information, we describe which preprocessing steps were performed.

## Preprocessing Pipeline:

1. Load `.eea` data into MNE.
2. Set standard 10-20 montage
3. Band-pass filter from `0.5 Hz` to the highest valid cutoff for this dataset.
4. Apply `50 Hz` notch filter.
5. Apply average EEG reference with `set_eeg_reference("average")`.
6. Downsample to `125 Hz`.
7. Fit ICA and run automatic EOG-like component detection with `ica.find_bads_eog`. `F3` was used as the EOG proxy for ICA-based artifacts removal.
8. Apply detected ICA exclusions.
9. Export as MNE raw FIF files 



