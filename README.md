# 🧠 Python Code Auto-Completer using Fine-Tuned CodeLlama

A lightweight code completion tool built by fine-tuning Meta's **CodeLlama-7B** model on Python code using QLoRA and HuggingFace’s PEFT techniques.

---

## 📌 Overview

This project demonstrates the training and deployment of a **Python code autocompletion model** fine-tuned on a subset of the CodeSearchNet dataset using [CodeLlama](https://huggingface.co/codellama/CodeLlama-7b-hf), Meta's large language model optimized for code.

> 🚀 The goal is to build a low-resource, efficient autocompletion assistant that predicts Python code tokens from docstrings and partial function definitions.

---

## 📂 Dataset

- **Name**: [`code_x_glue_tc_nl_code_search_adv`](https://huggingface.co/datasets/code_x_glue_tc_nl_code_search_adv)
- **Size Used**: 1000 samples
- **Language**: Python
- **Fields**: `docstring`, `code`

---

## 🛠️ Technologies Used

| Area | Tools |
|------|-------|
| Model | [CodeLlama-7B](https://huggingface.co/codellama/CodeLlama-7b-hf) |
| Training | QLoRA, PEFT, HuggingFace Transformers |
| Hosting | Hugging Face Hub |
| Notebook | Google Colab Pro (V100 GPU) |

---

## 🧪 Fine-Tuning Setup

- **Model**: `CodeLlama-7B`
- **PEFT Config**:
  - `r = 8`
  - `lora_alpha = 16`
  - `lora_dropout = 0.05`
- **Quantization**: 4-bit NF4 using `bitsandbytes`
- **Training**:
  - Epochs: `1` (due to GPU limitations)
  - Batch Size: `8`
  - Gradient Accumulation: `4`
  - Learning Rate: `2e-4`
  - Max Steps: `100`

### Example Prompt Template

```python
"[INST] Docstring: <your_docstring_here> [/INST] Code: <your_code_here>"
