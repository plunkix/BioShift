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
    F[Sparse Offline Data \n 'Batch 1'] -.->|Calibration Transfer| D
    D -->|Bias Corrected| E[Real-Time Concentration Prediction]
    E --> G[(Bioprocess Digital Twin)]
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style G fill:#bbf,stroke:#333,stroke-width:2px
    style D fill:#fcf,stroke:#333,stroke-width:2px