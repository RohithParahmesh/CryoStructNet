# CryoStructNet

**Deep 3D Protein Reconstruction from Unaligned Cryo-EM Projections**

![Python](https://img.shields.io/badge/Python-3.10-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Build](https://img.shields.io/badge/status-research--prototype-orange)

---

**CryoStructNet** is a deep learning framework for reconstructing high fidelity 3D protein density volumes directly from unaligned 2D Cryo-Electron Microscopy (Cryo-EM) projections. Inspired by Neural Radiance Fields (NeRF), our system learns to predict projection poses, fuse multi-view image features, and generate full 3D structures all without traditional alignment or averaging steps.

## Highlights

- View-conditioned volume prediction using NeRF-style positional encodings  
- Pose estimation network to infer projection orientation from raw images  
- Uncertainty-aware volume output with confidence maps  
- Trained on real Cryo-EM datasets (EMPIAR/EMDB) and synthetic simulations  

## Project Structure

```
CryoStructNet/
├── data/                  # Raw + processed Cryo-EM data
├── models/                # Pose estimator + volume decoder
├── training/              # Training scripts, loss functions
├── utils/                 # Metrics, visualization, I/O
├── notebooks/             # Demo + experiment logs
├── environment.yaml       # Conda environment specification
└── README.md              # Project overview
```

## Setup

### Using Conda (recommended)

```bash
git clone https://github.com/yourusername/CryoStructNet.git
cd CryoStructNet
conda env create -f environment.yaml
conda activate cryostructnet
```

> Note: If you plan to use simulated projection data, you may need to manually install [ASTRA Toolbox](https://www.astra-toolbox.com/docs/install.html) for tomographic projection support.

## Data

We use datasets from:

- EMPIAR – raw Cryo-EM images (e.g. EMPIAR-10061)
- EMDB – corresponding 3D density volumes
- Simulated projections from known 3D volumes using ASTRA Toolbox

## Training

```bash
python training/train.py --config training/config.yaml
```

Output includes:
- Reconstructed 3D volume  
- Voxel-wise confidence map  
- Pose predictions per projection  

## Evaluation

- Voxel-wise MSE  
- SSIM between prediction and ground truth  
- 3D correlation coefficient  
- Fourier Shell Correlation (FSC)  
- Visual inspection using ChimeraX or PyMOL  

## Results

I will put them up once I am done 

## TODO

- [ ] Pose estimation module  
- [ ] NeRF-style decoder  
- [ ] Volume + confidence head  
- [ ] Weak supervision on real Cryo-EM datasets  
- [ ] Paper-ready visualizations and metrics  

## Citation (Planned)

```bibtex
@article{rohith2025cryostructnet,
  title={CryoStructNet: Deep 3D Protein Reconstruction from Unaligned Cryo-EM Projections},
  author={Parahmesh, Rohith},
  journal={bioRxiv (preprint)},
  year={2025}
}
```

## License

MIT License.

## Acknowledgements

- CryoDRGN (UCSF)
- EMPIAR / EMDB datasets
- NeRF authors
- ASTRA Toolbox (tomographic projection simulation)
