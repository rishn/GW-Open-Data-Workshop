# GW-ODW Data Challenge 2 — Matched Filtering and Signal Recovery (Rookie)

<p align="center">
  <strong>Recover a weak gravitational-wave signal using matched filtering.</strong>
</p>

---

## Overview

Challenge 2 introduces matched filtering, the core technique used to detect modeled gravitational-wave signals buried in detector noise.

Using the `H1:CHALLENGE2` strain channel, this notebook demonstrates how to:

- Load and inspect the challenge dataset.
- Visualize the signal using a Q-transform.
- Generate a theoretical waveform template.
- Estimate the detector noise Power Spectral Density (PSD).
- Compute the matched-filter signal-to-noise ratio (SNR).
- Determine the merger time and peak SNR.

This challenge highlights how prior knowledge of the expected waveform can be used to detect signals that may not be obvious in the raw strain data.

---

## Notebook

**Notebook:** `GW_ODW_Data_Challenge_2.ipynb`

**Path:** `data_challenge/challenge_2/GW_ODW_Data_Challenge_2.ipynb`

---

## Challenge Objective

Analyze the provided strain data and recover the embedded binary black hole signal using matched filtering.

The challenge aims to determine:

1. The approximate merger time.
2. The peak matched-filter SNR.
3. The significance of the detection.

---

## Analysis Workflow

### 1. Load the Challenge Data

The frame file is loaded into a `gwpy.timeseries.TimeSeries` object to access the strain and metadata.

### 2. Visual Inspection with Q-Transform

A Q-transform spectrogram is generated to locate the candidate event in the time-frequency domain.

### 3. Generate a Waveform Template

A binary black hole waveform is created using `PyCBC` with representative component masses:

- $m_1 = 30\,M_\odot$
- $m_2 = 30\,M_\odot$

### 4. Estimate the Noise PSD

The detector noise Power Spectral Density is computed from the strain data.

### 5. Perform Matched Filtering

The template is correlated with the detector strain to produce an SNR time series.

### 6. Identify the Peak SNR

The time and value of the maximum SNR are used to estimate the event significance and merger time.

---

## Results

The matched-filter analysis identifies a strong binary black hole signal.

### Estimated Merger Time

The signal peaks at approximately:

**48.5 seconds from the start of the data segment**

### Peak Matched-Filter SNR

The maximum SNR is approximately:

**22.1**

### Detection Significance

An SNR above 20 indicates a highly significant detection, with excellent agreement between the observed data and the template waveform.

<p align="center">
  <img src="./snr_time_series.png" alt="Matched Filter SNR Time Series" width="900">
</p>

---

## Challenge Output

The notebook produces:

- Q-transform spectrogram.
- Template waveform.
- Estimated PSD.
- Matched-filter SNR time series.
- Peak SNR and corresponding merger time.

---

## Scientific Interpretation

Matched filtering maximizes sensitivity by weighting the correlation between the data and template by the inverse noise PSD:

$$
\rho(t) = \frac{(s|h)}{\sqrt{(h|h)}}.
$$

Where:

- $s$ is the detector strain.
- $h$ is the template waveform.
- $\rho(t)$ is the time-dependent signal-to-noise ratio.

A strong peak in $\rho(t)$ indicates that the template matches the data at that time.

---

## Tools and Libraries

- Python
- NumPy
- Matplotlib
- GWpy
- PyCBC
- LIGO Open Data

---

## Files

```text
data_challenge/
└── challenge_2/
    ├── GW_ODW_Data_Challenge_2.ipynb
    ├── challenge_2.md
    └── snr_time_series.png
```
---

### Learning Outcomes

After completing this challenge, you will be able to:

- Generate gravitational-wave templates.
- Estimate detector noise characteristics.
- Apply matched filtering.
- Interpret SNR time series.
- Quantify detection significance.

---

### References
- https://gwosc.org/
- https://gwpy.github.io/docs/stable/
- https://pycbc.org/

