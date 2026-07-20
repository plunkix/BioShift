# BioShift

> An open-source, modular Process Analytical Technology (PAT) pipeline translating high-dimensional Raman spectra into real-time bioprocess insights.

Commercial PAT systems often lock chemometric modeling behind closed ecosystems. **BioShift** provides a transparent, Python-native alternative designed specifically for upstream bioprocessing and digital twin architectures. 

It handles the complete mathematical translation of spectral data—from eliminating heavy culture media fluorescence via Savitzky-Golay derivatives, to extracting target analyte concentrations using Partial Least Squares (PLS) regression.

## 🚀 Key Features

*   **Spectral Pre-processing:** Implements Standard Normal Variate (SNV) and Savitzky-Golay filtering to eliminate baseline drift and background fluorescence.
*   **High-Dimensional PLS Engine:** Optimized Partial Least Squares regression for mapping hundreds of Raman shifts to singular target concentrations (e.g., Glucose, Lactate).
*   **One-Batch Transfer Learning (TLA):** Instantly localize a generalized base model to a new bioreactor environment using bias-correction algorithms on sparse offline reference data.

## 🧠 System Architecture

```mermaid
graph TD
    A[Raw Raman Spectra] --> B[Spectral Preprocessor]
    B -->|SNV + Savitzky-Golay| C[Processed Spectra]
    C --> D{BioShift PLS Engine}
    F[Sparse Offline Data<br/>From 'Batch 1'] -.->|Calibration Transfer| D
    D -->|Bias Corrected| E[Real-Time Predictions]
    E --> G[(Bioprocess Digital Twin)]
    
    style A fill:#E3F2FD,stroke:#0D47A1,stroke-width:2px,color:#0D47A1
    style B fill:#FFF3E0,stroke:#E65100,stroke-width:2px,color:#E65100
    style C fill:#FFF3E0,stroke:#E65100,stroke-width:2px,color:#E65100
    style D fill:#EDE7F6,stroke:#4A148C,stroke-width:2px,color:#4A148C
    style F fill:#F3E5F5,stroke:#4A148C,stroke-dasharray: 5 5,color:#4A148C
    style E fill:#E8F5E9,stroke:#1B5E20,stroke-width:2px,color:#1B5E20
    style G fill:#ECEFF1,stroke:#263238,stroke-width:2px,color:#263238