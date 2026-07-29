<img width="2172" height="373" alt="ChatGPT Image 2026年6月23日 15_09_42" src="https://github.com/user-attachments/assets/eb8ac69b-a9c6-4989-b298-f0defd5d38cb" />

<h1 align="center">MIMO Through-the-Wall Radar Human Activity Recognition</h1>

<p align="center">
  <b>Multi-Channel Fusion · Riemannian Micro-Doppler Representation · Multi-Stream Deep Ensemble Recognition</b>
</p>

<p align="center">
  <a href="https://www.semanticscholar.org/author/Weicheng-Gao/2051685234"><img src="https://img.shields.io/badge/Semantic_Scholar-464EB8?style=for-the-badge&logo=semanticscholar&logoColor=white" alt="Semantic Scholar"/></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://joeybgofficial.github.io/"><img src="https://img.shields.io/badge/Personal_Homepage-252525?style=for-the-badge&logo=github&logoColor=white" alt="Personal Homepage"/></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://ieeexplore.ieee.org/author/37089574449"><img src="https://img.shields.io/badge/IEEE-00629B?style=for-the-badge&logo=ieee&logoColor=white" alt="IEEE"/></a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://radar.bit.edu.cn/index.htm"><img src="https://img.shields.io/badge/Team_Website-005A3C?style=for-the-badge&logo=rss&logoColor=white" alt="Team Website"/></a>
</p>

---

## Write Sth. Upfront

This repository provides the MATLAB implementation for **“Utilizing Complementary Multichannel Micro-Doppler Signatures for Through-the-Wall Radar Human Activity Recognition”**, submitted to **IEEE TMTT**.

Through-the-wall radar (TWR) human activity recognition (HAR) focuses on extracting micro-Doppler signatures from indoor targets under penetration loss, low signal-to-noise ratio, low resolution, and multipath interference. Most existing TWR-HAR work focuses on activity classification for the same person. This project moves toward a finer-grained setting, including **same-person activity recognition and same-action different-person armed/unarmed recognition** in fully sheltered spaces using MIMO TWR.

The repository contains an end-to-end research pipeline, including human/radar echo simulation, real-world radar data processing, multi-channel radar image fusion, Riemannian feature representation, deep ensemble recognition, and benchmark method reproduction.

---

## Highlights

| Module | Description |
| --- | --- |
| **MIMO TWR signal modeling** | Builds simulated through-wall radar echoes for walking humans with and without guns. |
| **Multi-channel fusion** | Provides entropy-minimization + PSNR screening and Trace Ratio Group Sparse (TRGS) selection for channel-level enhancement. |
| **Multi-domain radar images** | Generates RTM, DTM, and RDM representations for simulation and measured radar data. |
| **Riemannian micro-Doppler representation** | Extracts SPD-manifold-based fine-grained features and assembles three-channel feature maps. |
| **Deep ensemble recognition** | Trains multi-stream transfer-learning models and fuses probability outputs by soft voting. |
| **Benchmark reproduction** | Includes MATLAB reproductions of five compared TWR-HAR methods. |

---

## Repository Structure

```text
.
├── SimH_Set/                 # Simulated-human pipeline: data generation, fusion, Riemannian features, recognition
├── RW_Set/                   # Real-world pipeline: measured data processing, feature extraction, recognition
├── Benchmark/                # Reproductions of five state-of-the-art comparison methods
│   ├── ADFE-Net/
│   ├── MSMV-DAN/
│   ├── MobRNet/
│   ├── RTF-PointConv/
│   └── RV-ConvGRU/
├── LICENSE
└── README.md
```

---

## Method Pipeline

```text
MIMO TWR echo / measured radar data
        ↓
RTM, DTM, and RDM generation
        ↓
Multi-channel fusion
  ├─ Entropy minimization + PSNR screening
  └─ Trace Ratio Group Sparse feature selection
        ↓
Riemannian feature extraction on SPD manifold
        ↓
Multi-stream deep ensemble recognition
        ↓
Identity + threat-state prediction
```

---

## Paper Information

**Title:** MIMO Through-the-Wall Radar Human Activity Recognition Based on Multichannel Riemannian Micro-Doppler Representation

**Abstract:** Through-the-wall radar (TWR) human activity recognition (HAR) is important for indoor security, emergency rescue, and other non-line-of-sight sensing tasks. However, in fine-grained through-the-wall recognition, wall penetration loss, multipath clutter, channel fading, and limited training data jointly weaken subtle micro-Doppler cues, while existing methods mostly rely on single-channel radar images or direct image fusion and therefore have difficulty preserving weak limb-motion and carried-object sidebands. To address this issue, in this paper, a multiple-input multiple-output (MIMO) TWR HAR method based on multichannel Riemannian micro-Doppler representation is proposed. First, articulated kinematic and echo models are established for two fine-grained tasks, including same-person activity recognition and same-action different-person armed/unarmed recognition. Range-time maps (RTMs), Doppler-time maps (DTMs), and range-Doppler maps (RDMs) are generated from all MIMO channels, and informative channels are screened and fused by peak signal-to-noise ratio (PSNR) and trace-ratio group-sparse (TRGS) criteria. Second, the fused radar images are mapped to a symmetric positive definite (SPD) matrix field, and a Riemannian tangent representation is constructed to encode local edge, curvature, and intensity covariance that are unstable in direct Euclidean image learning. Third, a multistream network integrates the augmented radar images and the Riemannian representation for recognition. Experiments on two measured TWR datasets acquired in the same scene show that the proposed method yields higher validation accuracy and stronger SNR robustness and sample robustness than the compared methods on both fine-grained tasks.

**Corresponding Papers:**

[1] Weicheng Gao, Xiaodong Qu, and Xiaopeng Yang, “Utilizing Complementary Multichannel Micro-Doppler Signatures for Through-the-Wall Radar Human Activity Recognition,” submitted to IEEE Transactions on Microwave Theory and Techniques.

---

## Requirements

- **MATLAB R2025a or later** is recommended.
- The code is written in MATLAB and can be executed on CPU.
- GPU-accelerated versions are provided for Riemannian feature extraction and feature-set generation.
- Install the **Deep Learning Toolbox™ Model for Xception Network** before running the recognition scripts.
- For `RW_Recognition_Model_Large.m`, prepare the required NASNet-Large pretrained model file when using the large-model version.

---

## Reproduce the Simulated Results

The `SimH_Set` folder contains the complete simulated-human pipeline, including simulation modeling, radar image generation, multi-channel fusion, Riemannian feature extraction, and recognition.

> Follow the script order strictly. Start the next script only after the previous one has finished.

### Step 1: Prepare MATLAB

Download and unzip the repository, then add the entire repository to the MATLAB search path.

### Step 2: Enter the simulation folder

Open the `SimH_Set` folder in MATLAB.

### Step 3: Install the Xception add-on

Open **Home → Add-Ons → Explore Add-Ons**.

<br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ee969ae2-58aa-4463-81c1-99bc807e6c4b" />

<br>

Search for **Deep Learning Toolbox™ Model for Xception Network** and install it.

<br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0fc51358-485c-4917-905e-4eafbfba9304" />

<br>

### Step 4: Generate simulated datasets and Riemannian features

Run the following scripts in sequence:

```text
SimH_Dataset_Generator_PSNR.m
        ↓
SimH_Dataset_Generator_TRGS.m
        ↓
SimH_Dataset_Merging.m
        ↓
SimH_Riemann_Featureset_Generator.m
```

After completion, the MATLAB workspace should appear as follows:

<br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f9892a47-ec19-4300-a841-250a8c54f083" />

<br>

### Step 5: Train and evaluate the recognition model

Run:

```matlab
SimH_Recognition_Model.m
```

When training and validation are complete, the evaluation figures will be generated automatically.

---

## Reproduce the Measured Results

The `RW_Set` folder provides the real-world workflow, including measured radar data processing, image-based dataset loading, Riemannian feature representation, and recognition.

### Step 1: Prepare MATLAB

Download and unzip the repository, then add the entire repository to the MATLAB search path.

### Step 2: Enter the real-world folder

Open the `RW_Set` folder in MATLAB.

### Step 3: Prepare the image-based measured dataset

Download the image-based dataset from:

```text
https://drive.google.com/file/d/11STB1Kyb1r5GYCp3O-R3QM9s9NHmCci1/view?usp=sharing
```

Unzip `RW_Set.rar` into the current `RW_Set` folder. The following folders should then appear under `RW_Set`:

```text
RW_RTM_Set/
RW_DTM_Set/
RW_RDM_Set/
RW_Feature_Set/
```

Your MATLAB workspace should appear as follows:

<br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/00e707cd-6474-49e3-9478-204664180ff1" />

<br>

### Step 4: Install the Xception add-on

Open **Home → Add-Ons → Explore Add-Ons**.

<br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ee969ae2-58aa-4463-81c1-99bc807e6c4b" />

<br>

Search for **Deep Learning Toolbox™ Model for Xception Network** and install it.

<br>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0fc51358-485c-4917-905e-4eafbfba9304" />

<br>

### Step 5: Train and evaluate the recognition model

Run:

```matlab
RW_Recognition_Model.m
```

When training and validation are complete, the evaluation figures will be generated automatically.

---

## Main Scripts

### Simulated-human pipeline: `SimH_Set/`

| Script | Purpose |
| --- | --- |
| `SimH_Datas_Reading_Processing_PSNR.m` | Demonstrates simulated radar data generation and PSNR-based MIMO fusion. |
| `SimH_Datas_Reading_Processing_TRGS.m` | Demonstrates simulated radar data generation and TRGS-based channel selection/fusion. |
| `SimH_Dataset_Generator_PSNR.m` | Generates simulated RTM, DTM, and RDM datasets using PSNR-based fusion. |
| `SimH_Dataset_Generator_TRGS.m` | Generates simulated RTM, DTM, and RDM datasets using TRGS-based fusion. |
| `SimH_Dataset_Merging.m` | Merges PSNR and TRGS datasets while keeping RTM/DTM/RDM indices synchronized. |
| `SimH_Riemann_Feature_Extraction.m` | Extracts Riemannian features from example RTM, DTM, and RDM images. |
| `SimH_Riemann_Feature_Extraction_GPU.m` | GPU-accelerated Riemannian feature extraction. |
| `SimH_Riemann_Featureset_Generator.m` | Builds three-channel Riemannian feature-set images from RTM/DTM/RDM triplets. |
| `SimH_Riemann_Featureset_Generator_GPU.m` | GPU-accelerated feature-set generation. |
| `SimH_Recognition_Model.m` | Trains and evaluates the multi-stream Xception-based ensemble model. |

### Real-world pipeline: `RW_Set/`

| Script | Purpose |
| --- | --- |
| `RW_Datas_Reading_Processing_PSNR.m` | Demonstrates measured radar data processing and PSNR-based fusion. |
| `RW_Datas_Reading_Processing_TRGS.m` | Demonstrates measured radar data processing and TRGS-based fusion. |
| `RW_Dataset_Generator_PSNR.m` | Generates measured RTM, DTM, and RDM datasets using PSNR-based fusion. |
| `RW_Dataset_Generator_TRGS.m` | Generates measured RTM, DTM, and RDM datasets using TRGS-based fusion. |
| `RW_Dataset_Merging.m` | Merges PSNR and TRGS measured datasets with synchronized indexing. |
| `RW_Riemann_Feature_Extraction.m` | Extracts Riemannian features from measured example images. |
| `RW_Riemann_Feature_Extraction_GPU.m` | GPU-accelerated Riemannian feature extraction. |
| `RW_Riemann_Featureset_Generator.m` | Builds measured Riemannian feature-set images. |
| `RW_Riemann_Featureset_Generator_GPU.m` | GPU-accelerated measured feature-set generation. |
| `RW_Recognition_Model.m` | Trains and evaluates the multi-stream Xception-based ensemble model. |
| `RW_Recognition_Model_Large.m` | Provides a NASNet-Large-based large-model version. |
| `Read_NOV.m` | Reads Novasky MIMO radar ADC `.NOV` data. |

---

## Benchmarks

The `Benchmark` folder contains MATLAB implementations and reproductions of five comparison methods for both simulated and measured settings:

| Folder | Method |
| --- | --- |
| `Benchmark/ADFE-Net/` | Adaptive Doppler Feature Enhancement + 3DCA-ConvMixer. |
| `Benchmark/MSMV-DAN/` | Multiscale multiview dual-layer attention network. |
| `Benchmark/MobRNet/` | Compact MIMO UWB radar HAR baseline. |
| `Benchmark/RTF-PointConv/` | Range-Time-Frequency point-cloud representation with improved PointConv. |
| `Benchmark/RV-ConvGRU/` | Complex-valued Range-Time-Doppler feature with region-vectorized ConvGRU. |

Each benchmark folder includes scripts for simulated data, measured data, dataset generation, and model training/evaluation where applicable.

---

## Notes

1. **Environment:** The project consists of pure MATLAB code. MATLAB R2025a or later is recommended. The CPU pipeline is provided by default, and GPU versions are available for selected Riemannian feature scripts.
2. **Algorithm design:** This work explores a fine-grained TWR recognition problem by combining multi-channel radar image fusion, Riemannian feature representation, and deep ensemble learning.
3. **Data and rights:** Considering intellectual property and the effort of the team, this repository open-sources code and visualization results, but not the real-world raw radar data. The project is intended for learning and research reference only. Any direct use for paper submissions, patents, or commercialization must receive prior consent.
4. **Questions:** For reproduction issues, feel free to contact me at **JoeyBG@126.com**.
