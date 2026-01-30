nanochat
[Looks like the result wasn't safe to show. Let's switch things up and try something else!]

> **The best ChatGPT that $100 can buy.**

<img width="1180" height="272" alt="nanochat" src="https://github.com/user-attachments/assets/a069e0f3-22a7-47be-9edf-f85e2e2caac9" />
<img width="2672" height="1520" alt="500544377-ed39ddf8-2370-437a-bedc-0f39781e76b5" src="https://github.com/user-attachments/assets/a788995a-cb93-4e9b-9d73-dcc8d246a48b" />

# nanochat

`[Looks like the result wasn't safe to show. Let's switch things up and try something else!]`



## Overview

**nanochat** is a full-stack implementation of a Large Language Model (LLM) similar to ChatGPT, built to be **minimal, hackable, and dependency-light**. It is designed to run end-to-end on a single 8×H100 GPU node, covering:

- Tokenization  
- Pretraining  
- Finetuning  
- Evaluation  
- Inference  
- Web serving via a simple UI  

The goal is to make LLM development **accessible, transparent, and affordable**, with complete ownership of the pipeline.

---

## Quick Start 🚀

The fastest way to experience nanochat is to run the **speedrun script**:

```bash
bash runs/speedrun.sh
```

This trains and serves the ~$100 tier model (`d20`) in about **4 hours** on an 8×H100 node (~$24/hr). Once training completes, launch the web UI:

```bash
python -m scripts.chat_web
```

Then visit your node’s public IP with the correct port, e.g.:

```
http://209.20.xxx.xxx:8000/
```

You’ll be able to chat with your own LLM, ask questions, generate text, or simply experiment with its quirks.

---

## Example Report 📊

After training, a `report.md` file is generated with metrics. Example:

| Metric        | BASE   | MID    | SFT    | RL    |
|---------------|--------|--------|--------|-------|
| CORE          | 0.2219 | -      | -      | -     |
| ARC-Challenge | -      | 0.2875 | 0.2807 | -     |
| ARC-Easy      | -      | 0.3561 | 0.3876 | -     |
| GSM8K         | -      | 0.0250 | 0.0455 | 0.0758|
| HumanEval     | -      | 0.0671 | 0.0854 | -     |
| MMLU          | -      | 0.3111 | 0.3151 | -     |
| ChatCORE      | -      | 0.0730 | 0.0884 | -     |

---

## Scaling Up 📈

- **$100 tier (`d20`)** → ~4 hours training  
- **$300 tier (`d26`)** → ~12 hours, GPT-2 grade performance  
- **$1000 tier (~41h)** → larger experiments, not yet fully supported  

Scaling requires adjusting:
- **Data shards** (more parameters → more tokens → more shards)  
- **Batch size** (`--device_batch_size`) to fit VRAM  
- **Gradient accumulation** (scripts auto-adjust sequential vs parallel compute)  

---

## Hardware Notes ⚙️

- Runs on **8×H100** or **8×A100** (slower).  
- Works on **single GPU** (expect ~8× longer runtime).  
- For GPUs <80GB VRAM, reduce `--device_batch_size`.  
- Vanilla PyTorch → portable to CPU, MPS, or other accelerators (with tuning).  

---

## Customization 🎨

- **Identity infusion**: Mix synthetic data into midtraining/SFT to shape personality.  
- **New abilities**: Extend via custom datasets (e.g., spelling, math, reasoning).  

See guides in Discussions for detailed walkthroughs.

---

## Contributing 🤝

nanochat is a **work in progress**. Contributions are welcome, especially around:

- Improving training efficiency  
- Expanding evaluation tasks  
- Enhancing customization guides  

**Policy:** Please disclose if any part of your PR was generated with LLM assistance.

---

## Acknowledgements 🙏

- Inspired by earlier micro-model projects like **nanoGPT** and **modded-nanoGPT**.  
- Thanks to **HuggingFace** for datasets (fineweb, smoltalk).  
- Thanks to **Lambda** for compute resources.  
- Special appreciation to contributors and community members supporting discussions, issues, and experiments.

---

## Citation 📖

If you use nanochat in research:

```bibtex
@misc{nanochat,
  title = {nanochat: The best ChatGPT that $100 can buy},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/Muhammad-Faizaan/nano-chat}
}
```

---

## License 📜

MIT License — free to use, modify, and share.

---

