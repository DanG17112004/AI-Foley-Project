# 🎬 FoleyCrafter Local Setup Guide

This guide documents the setup process for running **FoleyCrafter** locally on a Windows system with NVIDIA GPU support. It is intended to help team members reproduce the development environment with minimal effort.

---

# 🎯 Objective

Set up FoleyCrafter locally with GPU acceleration and understand the complete AI pipeline before integrating it into our major project.

---

# 🖥️ Tested Environment

| Component | Details |
|-----------|----------|
| Operating System | Windows |
| GPU | NVIDIA GeForce RTX 3050 Laptop GPU (4GB VRAM) |
| NVIDIA Driver | 580.97 |
| CUDA Version | 13.0 |

> **Note:** This guide may also work on other NVIDIA GPUs with compatible CUDA support.

---

# 📋 Prerequisites

Install the following software before starting:

- ✅ Miniconda
- ✅ Python
- ✅ Git
- ✅ Git LFS
- ✅ NVIDIA GPU Driver

---

# 🚀 Installation Steps

## 1. Clone the Repository

```bash
git clone <repository-url>
cd FoleyCrafter-main
```

---

## 2. Create the Conda Environment

```bash
conda env create -f requirements/environment.yaml
```

---

## 3. Activate the Environment

```bash
conda activate foleycrafter
```

---

## 4. Verify GPU Detection

Run:

```bash
nvidia-smi
```

Expected output should display:

- NVIDIA GPU information
- Installed Driver Version
- CUDA Version

---

## 5. Verify PyTorch

Run Python:

```python
import torch

print(torch.__version__)
print(torch.cuda.is_available())
```

Expected:

```text
True
```

If CUDA is unavailable (`False`), install the CUDA-enabled version of PyTorch.

---

# ⚠️ Common Issues & Solutions

## Conda Not Recognized

### Error

```text
'conda' is not recognized as an internal or external command
```

### Solution

Use **Anaconda Prompt** instead of the standard Windows Command Prompt.

---

## Network Timeout During Package Installation

Possible errors:

- ReadTimeoutError
- ConnectionResetError
- NameResolutionError

### Solution

- Ensure a stable internet connection.
- Re-run the installation command.
- Conda usually resumes the download automatically.

---

## CPU Version of PyTorch Installed

Check:

```python
import torch

print(torch.cuda.is_available())
```

If it returns:

```text
False
```

remove the CPU version of PyTorch and install the CUDA-enabled version.

---

# 📊 Current Progress

| Task | Status |
|------|--------|
| Required Software Installed | ✅ Completed |
| GPU Verified | ✅ Completed |
| Repository Downloaded | ✅ Completed |
| Conda Environment Created | ✅ Completed |
| Dependencies Installed | ✅ Completed |
| CUDA-enabled PyTorch | ⏳ Pending |
| Model Checkpoints Downloaded | ⏳ Pending |
| Gradio Demo Running | ⏳ Pending |
| First Foley Audio Generated | ⏳ Pending |

---

# 💡 Key Learnings

- Always use **Anaconda Prompt** when working with Conda.
- Successful GPU detection does not automatically mean PyTorch is using CUDA.
- Verify each installation step before moving to the next.
- Large AI models require sufficient storage and a stable internet connection.

---

# 🎯 Next Steps

- Install CUDA-enabled PyTorch
- Download FoleyCrafter model checkpoints
- Verify GPU support inside PyTorch
- Launch the Gradio demo
- Generate the first Foley audio
- Explore and understand the FoleyCrafter backend

---

# 👥 Team Notes

This guide was created as part of the **AI Foley Project** to ensure every team member can reproduce the same development environment. As the project evolves, this document will be updated with new findings, fixes, and improvements.

If you encounter an issue not covered here, please document the error and its solution so the guide can continue to improve.
