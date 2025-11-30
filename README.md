# Super-Resolution Playground (PyTorch)

This is a working prototype for a Single Image Super-Resolution (SISR) model I'm experimenting with.
It's currently a raw notebook focused on architecture implementation and training dynamics on the CelebA dataset.

### Technical Approach
The goal is to upscale low-res inputs (128x128) by a factor of 4x (to 512x512).

* **Upsampling Strategy:** Instead of standard Deconvolution (ConvTranspose), I used **PixelShuffle** (Sub-Pixel Convolution). It's more efficient for lightweight models and helps reduce checkerboard artifacts in the final output.
* **Backbone:** Residual Blocks (ResBlocks) with **Group Normalization** to stabilize training with smaller batch sizes.
* **Loss Function:** I chose **L1 Loss** over MSE because L1 tends to produce sharper edges and less blurry textures in image reconstruction tasks.

### Dataset
* **CelebA**: Used for training faces, handling resizing and gaussian blurring on-the-fly to create Low-Res/High-Res pairs.

### Status
This is a work-in-progress draft. The code includes the full training loop, model definition, and data loading pipeline.

---

### Visual Results (WIP)
Some preliminary results from the notebook.

**Sample 1: LR Input vs Model Output (SR) vs Ground Truth (HR)**
![Esempio 1](risultato_1.png)

**Sample 2:**
![Esempio 2](risultato_2.png)
