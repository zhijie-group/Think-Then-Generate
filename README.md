<div align="center">

# Think-Then-Generate: <br> Reasoning-Aware Text-to-Image Diffusion with LLM Encoders

[![arXiv](https://img.shields.io/badge/arXiv-2512.23576-b31b1b.svg)](xxx)
[![Hugging Face](https://img.shields.io/badge/🤗%20Hugging%20Face-Model-ffd21e)](https://huggingface.co/SJTU-Deng-Lab/Think-Then-Generate-T2I/tree/main)
[![Project Page](https://img.shields.io/badge/Website-Gallery-blue)](https://zhijie-group.github.io/Think-Then-Generate/)

<img src="assets/demo.png" width="100%">
More results can be found in the gallery(link).
</div>

---

## 🧠 How it Works

Most existing Text-to-Image (T2I) models act as simple **text-pixel mappers**—they encode text without truly understanding it. To bridge the gap between abstract user prompts and concrete visual pixels, we propose the **Think-Then-Generate** paradigm:

### 1. Phase I: Reasoning Activation
We first activate the reasoning potential of the LLM-based text encoder via lightweight SFT. Instead of directly passing the raw prompt to the generator, the LLM is encouraged to reason about the user's intent and rewrite the prompt into a detailed, structured description that serves as conditioning for the DiT decoders.

### 2. Phase II: Co-Evolution via Dual-GRPO
To ensure the reasoning actually improves image quality, we employ **Dual-GRPO** to co-optimize both the "Brain" (LLM) and the "Painter" (DiT Backbone):

* **For the LLM Encoder:** It is reinforced using **image-grounded rewards**. This forces the model to recall world knowledge and infer visual details that lead to better images.
* **For the Diffusion Backbone:** It is simultaneously pushed to produce images that are not just high-quality, but **semantically consistent** with the LLM's complex reasoning.

<img src="assets/pipeline.png" width="100%">

## 🛠️ Installation

Install the necessary dependencies:

```bash
pip install torch transformers diffusers accelerate
git clone https://github.com/zhijie-group/Think-Then-Generate.git
```

## 🚀 Inference

Run the model on a single GPU to experience reasoning-aware generation.

```bash
python inference.py \
  --model_path "SJTU-Deng-Lab/Think-Then-Generate-T2I" \
  --prompt "A multi-panel illustration showing the story of marking the boat to find a sword, with clear steps from dropping the sword to carving a mark on the boat." \
  --output "sword_result.jpg"

```


## 🖊️ Citation

If you find our work helpful, please consider citing:

```bibtex
@article{xxx,
  title={Think-Then-Generate: Reasoning-Aware Text-to-Image Diffusion with LLM Encoders},
  author={Authors},
  journal={arXiv preprint},
  year={2025}
}

```
