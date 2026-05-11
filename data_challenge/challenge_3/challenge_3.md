# GW-ODW Data Challenge 3 — Multi-Detector Matched Filtering (Intermediate)

<p align="center">
  <strong>Validate a gravitational-wave signal using coincident observations from multiple detectors.</strong>
</p>


---

## Overview

Challenge 3 extends the matched-filtering workflow to a multi-detector setting by analyzing data from both the Hanford (H1) and Livingston (L1) interferometers.

Using the `H1:CHALLENGE3` and `L1:CHALLENGE3` strain channels, this notebook demonstrates how to:

- Load and inspect data from multiple detectors.
- Estimate the noise Power Spectral Density (PSD).
- Generate a binary black hole waveform template.
- Perform matched filtering.
- Recover the signal time and peak signal-to-noise ratio (SNR).

This challenge illustrates how coherent detections across multiple detectors strengthen confidence in a gravitational-wave event.

---

## Notebook

### `./GW_ODW_Data_Challenge_3.ipynb`
<p>
  <a href="https://colab.research.google.com/github/rishn/GW-Open-Data-Workshop-2026/blob/main/data_challenge/challenge_3/GW_ODW_Data_Challenge_3.ipynb">
    <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open Challenge 3 in Colab">
  </a>
</p>

---

## Challenge Objective

Analyze the provided detector data and recover the embedded gravitational-wave signal using matched filtering.

The challenge aims to determine:

1. The time of the event.
2. The peak matched-filter SNR.
3. The consistency of the signal across detectors.

---

## Analysis Workflow

### 1. Load the Challenge Data

The challenge frame file is loaded into `gwpy.timeseries.TimeSeries` objects for both H1 and L1.

### 2. Inspect Detector Metadata

The notebook reports the sampling rate and duration of each time series.

### 3. Generate a Waveform Template

A compact binary coalescence template is generated using `PyCBC` with representative masses:

- $m_1 = 10\,M_\odot$
- $m_2 = 10\,M_\odot$

### 4. Estimate the Noise PSD

The PSD is computed for each detector and interpolated to match the template resolution.

### 5. Perform Matched Filtering

The template is correlated with the detector strain to compute the SNR time series.

### 6. Locate the Peak SNR

The maximum SNR and corresponding time are identified to estimate the event parameters.

---

## Results

The matched-filter analysis reveals a highly significant gravitational-wave signal.

### Estimated Event Time

The signal peaks at approximately:

**2478 seconds from the start of the data segment**

### Peak Matched-Filter SNR

The maximum SNR is approximately:

**29.0**

### Detection Significance

The strong SNR peak indicates an excellent match between the template waveform and the detector data.

<p align="center">
  <img src="./snr_time_series.png" alt="Matched Filter SNR Time Series" width="900">
</p>

---

## Challenge Output

The notebook produces:

- Detector metadata summaries.
- PSD estimates.
- Template waveform.
- Matched-filter SNR time series.
- Peak SNR and event time.

---

## Scientific Interpretation

Matched filtering computes the noise-weighted correlation between the data and a waveform template:

$$
\rho(t) = \frac{(s|h)}{\sqrt{(h|h)}}.
$$

A strong peak in $\rho(t)$ indicates the presence of a signal consistent with the modeled binary merger.

Observing the same event in multiple detectors significantly increases confidence in the detection and enables sky localization.

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
└── challenge_3/
    ├── GW_ODW_Data_Challenge_3.ipynb
    ├── challenge_3.md
    └── snr_time_series.png
```
---

### Learning Outcomes

After completing this challenge, you will be able to:

- Analyze data from multiple gravitational-wave detectors.
- Generate and apply waveform templates.
- Estimate detector PSDs.
- Compute matched-filter SNR time series.
- Interpret coincident detections across observatories.

---

### References
- https://gwosc.org/
- https://gwpy.github.io/docs/stable/
- https://pycbc.org/

