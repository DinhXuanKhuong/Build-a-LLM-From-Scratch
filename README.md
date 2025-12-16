# Build a LLM From Scratch

This repo contains my implementations from the book “Build a LLM from Scratch”. It includes step-by-step notebooks that cover tokenization, dataset preparation, and a GPT-style model implemented with PyTorch, along with small demo datasets.

## Repo Structure
- `all_in_one.ipynb`: End-to-end walkthrough starting from simple tokenization up to training and generation.
- `gpt.ipynb`: Focused notebook implementing and training a GPT-style model (embedding, attention blocks, layer norm, MLP, generation, checkpoints).
- `data/`: Sample text corpora (e.g., `the-verdict.txt`, `harrypotter.txt`).


## Requirements
These notebooks use Python and PyTorch. From the notebooks’ imports, you’ll likely need:
- `torch` (PyTorch)
- `tiktoken`
- `matplotlib`
- Jupyter (to run notebooks)

Example environment setup on Linux (bash):
```bash
# create and activate a virtual environment (optional but recommended)
python3 -m venv .venv
source .venv/bin/activate

# install packages
pip install --upgrade pip
pip install torch tiktoken matplotlib jupyter
```

GPU acceleration is automatic if your PyTorch install detects CUDA; otherwise it runs on CPU.

## Datasets
Place your plain-text training files inside `data/`. Two samples are included:
- `data/the-verdict.txt`
- `data/harrypotter.txt`

You can swap in your own `.txt` files and point the corresponding cells in the notebooks to them.

## How to Run
You can run either notebook; both are self-contained. Recommended flow:

1) Open the repo in VS Code and use the built-in Jupyter support, or start Jupyter locally:
```bash
jupyter lab  # or: jupyter notebook
```

2) Open and run cells in:
- `all_in_one.ipynb` for a progressive, didactic path from tokenization through training/generation.
- `gpt.ipynb` for a focused GPT implementation with configuration, training loop, and text generation helpers.

3) Generation (in `gpt.ipynb`):
- The notebook defines tokenization helpers and a `generate(...)` routine. After training or loading a checkpoint, run the generation cell and provide a prompt string. Adjust parameters such as `max_new_tokens`, `top_k`, and `temperature` in the `generate` call.

## Tips
- Start with a very small config (context length, layers, heads) to verify the training loop and generation path, then scale up.
- Use CPU for quick sanity checks; switch to GPU for speed once things work.
- If you change the tokenizer (e.g., custom vocab vs `tiktoken` GPT-2 BPE), re-create datasets and keep the tokenizer consistent for training and inference.


## License
This repository contains personal study implementations based on the book’s concepts and public datasets. Use the included data responsibly and respect the original content’s copyrights.
