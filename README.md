# SSVEP-Based Speller using Empirical Mode Decomposition (EMD) 🧠 

This repository presents the final project of the **Advanced Signal Processing in Medicine** and **Neuroengineering** courses, conducted at the **Universitat Politècnica de València** (2022).  

The project was developed by  
**Elisa Vasta**, **Arianna Luraschi**, **Javier Quirant Agulló**, and **Hatem Benmechiche**.

---

## 📘 Project Overview

The goal of this work was to design a **Brain–Computer Interface (BCI) speller** based on **Steady-State Visual Evoked Potentials (SSVEP)** — EEG responses to repetitive visual stimuli — using **Empirical Mode Decomposition (EMD)** for signal processing and classification.

The system associates the **EEG response frequency** to the **flickering frequency** of visual targets displayed on a matrix-based interface, enabling users to select letters or symbols using only their visual attention.  
This approach contributes to assistive communication technologies for patients with **motor or speech impairments**.

---

## 🧩 Methodology

### 🎯 Experimental Setup
- **Dataset:** [A Benchmark Dataset for SSVEP-Based BCIs (Tsinghua BCI Lab, Wang et al., 2017)]  
- **Participants:** 35 healthy subjects (12 used for this study)  
- **Stimulation interface:** 5×8 character matrix (40 targets)  
- **Frequencies:** 8–15.8 Hz (step 0.2 Hz)  
- **Trial structure:**
  - 0.5 s cue  
  - 5 s visual stimulation  
  - 0.5 s blank interval  
- **Acquisition system:**  
  - 64-channel EEG (10–20 system)  
  - Sampling rate: 1000 Hz  
  - Reference: Cz  
  - Bandwidth: 0.15–200 Hz  
  - Notch filter: 50 Hz  

---

### ⚙️ Signal Processing

- **Preprocessing:**  
  - Downsampled to 250 Hz  
  - No additional digital filtering  
  - Analysis performed during the 0.5s blank period following each visual cue  

- **Feature Extraction via Empirical Mode Decomposition (EMD):**  
  - EEG decomposed into Intrinsic Mode Functions (IMFs)  
  - IMFs 2 and 3 (and optionally 4–5) selected as most representative of the stimulus frequency range (8–45 Hz)  

- **Classification:**  
  - FFT applied to combined IMFs  
  - Peaks detected using 70% height threshold  
  - The first peak frequency compared with the known stimulus frequencies to assign the corresponding character  

---

## 📈 Results

| IMF Combination | Accuracy (Single Run) | Accuracy (Averaged) |
|------------------|-----------------------|----------------------|
| IMFs 2 + 3       | 27.5%                | 78.12%               |
| (IMFs 2 + 3) - (4 + 5) | **34.38%**        | **82.29%**           |

- Averaging across trials greatly improved the signal-to-noise ratio (SNR) and classification accuracy.  
- Single-trial performance (~34%) was comparable to state-of-the-art results for traditional EMD methods with fewer classes.  
- The method achieved recognition across **40 different characters** without a dedicated calibration phase.

---

## 🧠 Discussion

- The EMD-based method successfully extracted relevant frequency components corresponding to SSVEP responses.  
- The accuracy is limited in single-trial (online) scenarios but demonstrates the feasibility of **low-cost, training-free** SSVEP spellers.  
- Averaging trials (offline mode) reached performance similar to existing literature benchmarks.

---

## 🚀 Future Work

- Combine EMD with **Canonical Correlation Analysis (CCA)** or **Decision Tree** classifiers for higher accuracy.  
- Include **word prediction dictionaries** to increase spelling speed.  
- Compute **Information Transfer Rate (ITR)** and compare with P300 and hybrid BCI paradigms.  
- Explore real-time implementation and adaptive calibration for user-specific parameters.

---

## ⚖️ Limitations

- **Communication speed** remains low - only a few letters per minute in single-trial setups.  
- **Ocular fatigue** and **visual dependency** restrict usability for some patients.  
- **Signal variability** across subjects limits generalization.  
- **EEG noise** and spontaneous activity may obscure SSVEP harmonics.  

---

## 🧬 Ethical Considerations

The project highlights key ethical aspects of BCI development:
- Respect for **informed consent** and participant autonomy  
- Protection of **neural data privacy** (“right to brain privacy”)  
- Awareness of human–machine integration and potential **identity alteration** concerns  
- Promotion of assistive, non-invasive communication tools for people with motor impairments  

---

## 📄 Files in this Repository

- `SSVEP_speller_report.pdf` — Full academic report  
- `SSVEP_speller_presentation.pdf` — Final presentation slides  

The project code is currently not publicly released.
If you are interested in accessing the code or replication details, please contact the author.

---

## ✉️ Contact

**Elisa Vasta**  
📧 elisa.vasta@mail.polimi.it  

Code and experimental scripts are available upon request.

---

## 📚 References

Key references:
- Wang et al. (2017) *A Benchmark Dataset for SSVEP-Based Brain–Computer Interfaces*  
- Chen et al. (2015) *High-speed spelling with a noninvasive BCI*  
- Tello et al. (2014) *Comparison of new techniques based on EMD for control of a SSVEP-BCI*  
- Volosyak (2011) *SSVEP-based Bremen–BCI interface—boosting information transfer rates*  

For the full bibliography, refer to the attached report.

---
