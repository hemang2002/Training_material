# Train → Optimize → Serve → Containerize → Deploy

## 📁 Folder map

| Folder | What's inside | Start with |
|---|---|---|
| [`Day1_PyTorch_Fundamentals/`](Day1_PyTorch_Fundamentals/) | tensors & autograd, training loop, CNN on FashionMNIST, lab | `README.md` |
| [`Day2_Transfer_Learning_and_Optimization/`](Day2_Transfer_Learning_and_Optimization/) | MobileNetV2 fine-tuning, dynamic/static/QAT quantization, pruning, FP16, ONNX + ONNX Runtime INT8, lab, one-command `scripts/train_and_export.py`; extra notebooks: data augmentation, image segmentation (Penn-Fudan, U-Net vs pretrained LR-ASPP), RNN/LSTM text classification (SMS spam) | `README.md` |
| [`Day3_Serving_Flask_Streamlit/`](Day3_Serving_Flask_Streamlit/) | Flask API, Streamlit UI, tests, API notebooks, server-side LAB | `README.md` |
| [`Training_Visualized/`](Training_Visualized/) | 16 interactive, offline HTML lessons (model → gradient descent → backprop → training loop → activations & softmax → NN playground → overfitting → dropout & BatchNorm → metrics → CNN → transfer learning → quantization/pruning/distillation → data augmentation → image segmentation → RNN & LSTM → reinforcement learning), Simple/Detailed view | `index.html` |
| [`Docker_K8s_Visualized/`](Docker_K8s_Visualized/) | 13 interactive, offline HTML pages for Day 4 (install Docker Desktop → why containers → images & layers → running containers → compose → why Kubernetes → Pod → Deployment → Service → ConfigMap/Secret → probes & resources → autoscaling → hands-on lab with real command output) | `index.html` |
| [`References/`](References/) | 150+ verified links (docs, papers, tutorials, videos) by topic + free cloud comparison | `README.md` |
| `models/` | the Day-2 output shared by Days 3–4: `model_fp32.onnx`, `model_int8.onnx`, `model_card.json`, `labels.json` | — |
| `data/` | datasets, downloaded automatically (git-ignored) | — |

## ⚙️ Setup

Python 3.10–3.13. Students are expected to know how to install Python and create environments.

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate        Linux/macOS: source .venv/bin/activate
pip install torch torchvision --index-url https://download.pytorch.org/whl/cpu    # CPU build (small); GPU: see pytorch.org
pip install -r requirements.txt
python -m ipykernel install --user --name ml-course --display-name "Python (ml-course)"
```
