# Quantum-Inspired Modelling of OPM-MEG Brain Activity Using Matrix Product States

Master's Thesis

Author: Fatemah Abdelwahed

Supervisor: Mehrnoosh Sadrazadeh

University: UCL

---

## Overview

This project investigates the use of Matrix Product States (MPS), a tensor-network representation originating from quantum many-body physics, for modelling Optically Pumped Magnetometer Magnetoencephalography (OPM-MEG) recordings.

The pipeline converts continuous OPM-MEG recordings into trial-based tensors before applying several tensor decomposition methods:

- CP decomposition
- Tucker decomposition
- Tensor Train (Matrix Product State)
  
- Reconstruction error analysis
- Compression analysis

The objective is to determine whether quantum-inspired tensor network representations provide an efficient representation of high-dimensional MEG data.

---

## Dataset

VBMEG OPM-MEG Dataset

Subjects

- 002
- 005
- 006
- 093

Tasks

- Auditory
- Somatosensory
- Motor
- Rest

Sampling frequency

2000 Hz

Sensors

15 OPM sensors

30 measurement channels

The dataset is not distributed with this repository.

Download it from

https://vbmeg.atr.jp/nictitaku209/#download

and place it inside

data/raw/

---

## Repository Structure

OPM-MEG-MPS/
│
├── README.md
├── .gitignore
│
├── data/
│   ├── raw/                     
│   │   ├── 002/
│   │   │   ├── OPM/
│   │   │   │   ├── Auditory
│   │   │   │   ├── Motor
│   │   │   │   ├── Rest
│   │   │   │   └── Somatosensory
│   │   │   ├── EEG/
│   │   │   ├── SQUID/
│   │   │   └── T1/
│   │   ├── 005/
│   │   ├── 006/
│   │   ├── 093/
│   │   └── 095/
│   │
│   ├── loaded/
│   │   ├── 002/
│   │   ├── 005/
│   │   ├── 006/
│   │   └── 093/
│   │
│   └── preprocessed/
│       ├── 002/
│       ├── 005/
│       ├── 006/
│       └── 093/
│    
│   
│
├── notebooks/
│   ├── 01_load_data.ipynb
│   ├── 02_preprocess_data.ipynb
│   ├── 03_tensor_decomposition.ipynb
│   ├── 04_mps.ipynb
│   └── exploratory/
│
├── src/
│   ├── data_loader.ipynb
│   ├── preprocess_data.ipynb
│   └── tensor_decomposition.ipynb
│
└── results/
    ├── cp/
    ├── tucker/
    ├── tt/
    ├── mps/
    └── comparison/

---

## Pipeline

Raw MATLAB files

↓

Load

↓

NPZ conversion

↓

Filtering

↓

Event detection

↓

Epoching

↓

Tensor

↓

CP

↓

Tucker

↓

Tensor Train (MPS)

↓

Evaluation