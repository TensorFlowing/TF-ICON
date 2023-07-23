# TF-ICON: Diffusion-Based Training-Free Cross-Domain Image Composition (ICCV 2023)

This repo contains the official implementation for the paper Diffusion-Based Training-Free Cross-Domain Image Composition (ICCV 2023)

> **TF-ICON: Diffusion-Based Training-Free Cross-Domain Image Composition**<br>
<!-- > [Gwanghyun Kim](https://gwang-kim.github.io/), Taesung Kwon, [Jong Chul Ye](https://bispl.weebly.com/professor.html) <br> -->
> Shilin Lu, Yanzhu Liu, and Adams Wai-Kin Kong
> CVPR 2022
> 
>**Abstract**: <br>
Text-driven diffusion models have exhibited impressive generative capabilities, enabling various image editing tasks. In this paper, we propose TF-ICON, a novel Training-Free Image COmpositioN framework that harnesses the power of text-driven diffusion models for cross-domain image-guided composition. This task aims to seamlessly integrate user-provided objects into a specific visual context. Current diffusion-based methods often involve costly instance-based optimization or finetuning of pretrained models on customized datasets, which can potentially undermine their rich prior. In contrast, TF-ICON can leverage off-the-shelf diffusion models to perform cross-domain image-guided composition without requiring additional training, finetuning, or optimization. Moreover, we introduce the exceptional prompt, which contains no information, to facilitate text-driven diffusion models in accurately inverting real images into latent representations, forming the basis for compositing. Our experiments show that equipping Stable Diffusion with the exceptional prompt outperforms state-of-the-art inversion methods on various datasets (CelebA-HQ, COCO, and ImageNet), and that TF-ICON surpasses prior baselines in versatile visual domains.

<!-- ## [<a href="https://pnp-diffusion.github.io/" target="_blank">Project Page</a>] [<a href="https://github.com/MichalGeyer/pnp-diffusers" target="_blank">Diffusers Implementation</a>] -->

<!-- [![arXiv](https://img.shields.io/badge/arXiv-PnP-b31b1b.svg)](https://arxiv.org/abs/2211.12572) [![Hugging Face Spaces](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Spaces-blue)](https://huggingface.co/spaces/hysts/PnP-diffusion-features) <a href="https://replicate.com/arielreplicate/plug_and_play_image_translation"><img src="https://replicate.com/arielreplicate/plug_and_play_image_translation/badge"></a> [![TI2I](https://img.shields.io/badge/benchmarks-TI2I-blue)](https://www.dropbox.com/sh/8giw0uhfekft47h/AAAF1frwakVsQocKczZZSX6La?dl=0) -->

![tf-icon](assets/tf-icon.png)

<!-- # Updates:

**19/06/23** 🧨 Diffusers implementation of Plug-and-Play is available [here](https://github.com/MichalGeyer/pnp-diffusers). -->

## TODO:
<!-- - [ ] Diffusers support and pipeline integration
- [ ] Gradio demo -->
- [ ] Release TF-ICON Test Benchmark


<!-- ## Usage

**To plug-and-play diffusion features, please follow these steps:**

1. [Setup](#setup)
2. [Feature extraction](#feature-extraction)
3. [Running PnP](#running-pnp)
4. [TI2I Benchmarks](#ti2i-benchmarks) -->


## Setup

Our codebase is built on [Stable-Diffusion](https://github.com/Stability-AI/stablediffusion)
and has shared dependencies and model architecture. VRAM of 24 GB+ are required. 

### Creating a Conda Environment

```
conda env create -f tf_icon_env.yaml
conda activate tf-icon
```

### Downloading Stable-Diffusion Weights

Download the StableDiffusion weights from the [Stability AI at Hugging Face](https://huggingface.co/stabilityai/stable-diffusion-2-1-base/blob/main/v2-1_512-ema-pruned.ckpt)
(download the `sd-v2-1_512-ema-pruned.ckpt` file), and put it under `./ckpt` folder.

## Running TF-ICON

### Data Preparation

Several input samples are avaliable under `./inputs` directory. Each sample involves one background (bg), one foreground (fg), one segmentation mask for the foreground (fg), and one user mask that denotes the desired composition location. Note that the resolution of the input foreground should not be too small. 

- Cross domain: the background (bg) and foreground (fg) images originate from different visual domains.
- Same domain: both the background (bg) and foreground (fg) images belong to the photorealism domain.

### Image Composition
To execute the TF-ICON, run the following commands:

```
python main_tf_icon.py  --ckpt <path/to/model.ckpt/>      \
                        --root ./inputs/cross_domain      \
                        --cross_domain True               \
                        --dpm_steps 20                    \
                        --dpm_order 2                     \
                        --scale 5                         \
                        --outdir ./outputs                \
                        --gpu cuda:0                      \
                        --seed 3407                         
```
- `ckpt`: The path to the checkpoint of Stable Diffusion.
- `root`: The path to your input data.
- `cross_domain`: Setting if the foreground and background are from different visual domains. 
- `dpm_steps`: The diffusion sampling steps.
- `dpm_solver`: The order of the probability flow ODE solver.
- `scale`: The classifier-free guidance (CFG) scale.


## TF-ICON Test Benchmark

To-DO.
<!-- You can find the **Wild-TI2I**, **ImageNetR-TI2I** and **ImageNetR-Fake-TI2I** benchmarks in [this dropbox folder](https://www.dropbox.com/sh/8giw0uhfekft47h/AAAF1frwakVsQocKczZZSX6La?dl=0). The translation prompts and all the necessary configs (e.g. seed, generation prompt, guidance image path) are provided in a yaml file in each benchmark folder. -->

<!-- 
## Citation
```
@InProceedings{Tumanyan_2023_CVPR,
    author    = {Tumanyan, Narek and Geyer, Michal and Bagon, Shai and Dekel, Tali},
    title     = {Plug-and-Play Diffusion Features for Text-Driven Image-to-Image Translation},
    booktitle = {Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)},
    month     = {June},
    year      = {2023},
    pages     = {1921-1930}
}
``` -->
