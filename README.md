# CryoStructNet

**Deep 3D Protein Reconstruction from Unaligned Cryo-EM Projections**

![Python](https://img.shields.io/badge/Python-3.10-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Build](https://img.shields.io/badge/status-research--prototype-orange)

---

**View2Volume** is a deep learning framework for reconstructing high-fidelity 3D protein density volumes directly from unaligned 2D Cryo-Electron Microscopy (Cryo-EM) projections. Inspired by Neural Radiance Fields (NeRF), our system learns to predict projection poses, fuse multi-view image features, and generate full 3D structures — all without traditional alignment or averaging steps.

## Highlights

- View-conditioned volume prediction using NeRF-style positional encodings  
- Pose estimation network to infer projection orientation from raw images  
- Uncertainty-aware volume output with confidence maps  
- Trained on real Cryo-EM datasets (EMPIAR/EMDB) and synthetic simulations  

## Setup

```bash
git clone https://github.comRohithParahmesh/CryoStructNet.git
cd CryoStructNet
conda create -n cryo3d python=3.10
conda activate cryo3d
pip install -r requirements.txt
```
## Data

We use datasets from:
- EMPIAR – raw Cryo-EM images (e.g. EMPIAR-10061)
- EMDB – corresponding 3D density volumes
- Simulated projections from known 3D volumes using ASTRA Toolbox

## Training 
```bash
python training/train.py --config training/config.yaml
```

## Evaluation
-Voxel-wise MSE
-SSIM between prediction and ground truth
-3D correlation coefficient
-Fourier Shell Correlation (FSC)
-Visual inspection using ChimeraX or PyMOL
