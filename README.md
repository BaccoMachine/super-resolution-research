# Super-Resolution Prototype (PyTorch)

This is a working prototype for a Single Image Super-Resolution (SISR) model I'm experimenting with.
It's currently a raw notebook focused on architecture implementation and training dynamics on the CelebA dataset.

### Technical Approach
The goal is to upscale low-res facial images (128x128) by a factor of 4x (to 512x512).

* **Upsampling Strategy:** Instead of standard Deconvolution (ConvTranspose), I implemented **PixelShuffle** (Sub-Pixel Convolution). This allows the model to learn upscaling filters directly in the low-resolution space, significantly reducing computational cost and checkerboard artifacts.
* **Loss Function:** Optimized using **L1 Loss** to encourage sharper edge reconstruction compared to MSE (which typically results in blurry textures).

### Model
I designed the architecture to be extremely lightweight but dense in feature representation:

* **Parameter Count:** **134,199**. This makes the model extremely efficient compared to standard SR models (often >1M params).
* **Latent Dimension:** **64 feature channels**. The model projects the RGB input into a 64-dimensional feature space before the residual blocks to capture high-frequency details.
* **Hardware Setup:** Training pipeline implemented with PyTorch `DataParallel`, optimized to run on a **Dual-GPU** cluster.

### Dataset
* **CelebA**: Used for training faces, handling resizing and gaussian blurring on-the-fly to create Low-Res/High-Res pairs.

### Status
This is a work-in-progress draft. The code includes the full training loop, model definition, and data loading pipeline in a single notebook.

---

### Visual Results (WIP)
Preliminary results from the latest training epoch.

**Sample 1: LR Input vs Model Output (SR) vs Ground Truth (HR)**
![Result 1](risultato_1.png)

**Sample 2:**
![Result 2](risultato_2.png)
