# Quantum-Inspired Modelling of OPM-MEG Brain Activity using Tensor Decomposition and Variational Quantum Circuit Classification

Master's Thesis

Author: Fatemah Abdelwahed

Supervisor: Mehrnoosh Sadrazadeh & Umesh Vivekananda

University: UCL

---

## Overview

This project investigates tensor-based and quantum-inspired approaches for modelling Optically Pumped Magnetometer Magnetoencephalography (OPM-MEG) recordings.

The project focuses on representing high-dimensional sensor-level OPM-MEG recordings as tensors and evaluating whether tensor decomposition methods can provide compact representations while preserving information relevant to the underlying neural signals and classification.

The pipeline consists of two main stages:

- Tensor decomposition
- Variational Quantum Circuit (VQC) classification

The tensor decomposition stage compares:

- CP decomposition
- Tucker decomposition
- Tensor Train (TT) decomposition

The Tensor Train representation is closely related to the Matrix Product State (MPS) representation used in quantum many-body physics.

The decomposed representations are evaluated using reconstruction and compression metrics before being used as inputs to a VQC classification pipeline.

---

## Project Objectives

The main objectives are to:

- preprocess OPM-MEG recordings into trial-based data;
- represent the recordings as multidimensional tensors;
- investigate CP, Tucker and Tensor Train decompositions;
- evaluate the trade-off between compression and information preservation;
- compare decomposition performance across subjects and experimental tasks;
- construct compact feature representations from Tensor Train decompositions;
- apply dimensionality reduction and feature normalisation;
- encode the resulting features into quantum states using angle encoding;
- investigate Variational Quantum Circuit classification;
- evaluate VQC performance using subject-independent validation.
  
---

## Dataset

The project uses the VBMEG OPM-MEG dataset.

The dataset contains OPM-MEG recordings from multiple experimental tasks. The subjects used in the experiments are:
- 002
- 005
- 006
- 093

Experimental Tasks:
- Auditory
- Somatosensory
- Motor
- Rest
  
OPM-MEG Configuration:
- Sampling frequency: 2000 Hz
- OPM sensors: 15
- Measurement channels: 30
Two measurement axes are recorded for each OPM sensor.

The analysis is performed at the sensor level. No source reconstruction is performed.

The dataset is not distributed with this repository.

The VBMEG dataset can be obtained from:

https://vbmeg.atr.jp/nictitaku209/#download

After downloading the relevant data, place the raw dataset under:

data/raw/

---

## Tensor Decomposition

Three tensor decomposition approaches are investigated:
- CP Decomposition: represents a tensor as a sum of rank-one tensors.
- Tucker Decomposition: represents a tensor using a smaller core tensor and factor matrices.
- Tensor Train / Matrix Product State: factorises a tensor into a sequence of lower-order cores connected by TT-ranks.

In the context of quantum many-body physics, the Tensor Train representation is commonly referred to as a Matrix Product State (MPS).

The Tensor Train representation is particularly relevant to this project because it provides a connection between tensor-network methods and quantum-inspired representations.

---

## VQC Classification

The VQC experiments investigate whether compact tensor-derived features can be used for quantum circuit-based classification.

The quantum circuit consists of:
- angle-based feature encoding;
- trainable variational parameters;
- variational layers;
- qubit entanglement;
- measurement of the quantum state;
- classical loss-based optimisation.

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
│   │   │   ├── Auditory
│   │   │   |   ├── run01.npz
|   |   |   |   └── run02.npz
│   │   │   ├── Motor
│   │   │   ├── Rest
│   │   │   └── Somatosensory
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
├── results/
│   ├── decomposition_experiment1
│   |   ├── Plots
|   |   └── tensor_decomposition_results.xlsv
│   ├── decomposition_experiment2
│   ├── tt_rank_selection
│   └── vqc
│
└── src/
    ├── data_loader.ipynb
    ├── preprocess_data.ipynb
    ├── preVQC.ipynb
    ├── tensor_decomposition.ipynb
    ├── TT_rank.ipynb
    ├── VQC_experiment1.ipynb
    └── VQC_experiment2.ipynb
