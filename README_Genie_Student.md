
### 🧬 Genie (Student Replication)

This is a student replication of **Genie: Generating Novel, Designable, and Diverse Protein Structures by Equivariantly Diffusing Oriented Residue Clouds**, originally presented at ICML 2023 by Yeqing Lin and Mohammed AlQuraishi. This project reproduces and extends the model for generative protein backbone design using denoising diffusion models and SE(3)-equivariant neural networks.

---

## 📚 Paper Reference

> **Genie**: [arXiv:2301.12485](https://arxiv.org/abs/2301.12485)  
> Authors: Yeqing Lin, Mohammed AlQuraishi  
> Year: 2023

---

## 📦 Project Structure

```bash
genie-main/
├── genie/                     # Model, diffusion, and config files
├── scripts/                   # Data downloading, evaluation setup
├── evaluations/               # Evaluation pipeline using ProteinMPNN + ESMFold
├── pretrained_model/          # Pretrained weights and config
├── runs/                      # Training run outputs
├── sample.py                  # Structure generation entry point
├── train.py                   # Training entry point
└── README.md                  # You're reading this!
```

---

## 🧪 Environment Setup

### 1. Clone the Repository

```bash
git clone https://github.com/<your-username>/genie-protein-design.git
cd genie-protein-design
```

### 2. Install Required Packages

```bash
pip install -e .
```

---

## 🚀 Training the Model

1. Set up a configuration file in `runs/[RUN_NAME]/configuration`
2. Launch training:

```bash
python genie/train.py -c runs/RUN_NAME/configuration -g0 &
```

You can find config examples in `example_configuration` and full parameter options in `genie/config.py`.

---

## 🎯 Sampling New Structures

To generate backbone samples from a trained model:

```bash
python genie/sample.py -n RUN_NAME -g0
```

Outputs are stored under:

```
runs/[RUN_NAME]/version_[VERSION]/samples/epoch_[EPOCH]
```

---

## 📊 Evaluation

To evaluate generated samples:

```bash
./scripts/setup_evaluation_pipeline.sh
python evaluations/pipeline/evaluate.py --input_dir INPUT_DIR --output_dir OUTPUT_DIR
```

Inputs should include `coords/` with Cα atom coordinates.

---

## 📚 Dataset

We used the **SCOPe** and **AlphaFold-SwissProt** datasets. The included script:

```bash
./scripts/install_dataset.sh
```

downloads and preprocesses the data.

---

## 🙋‍♀️ Project Info

- **Project Name:** Genie Student Implementation
- **Course:**Data Science Engineering Methods and Tools (Spring 2025)
- **Institution:** Northeastern University
- **Contributors:** Rahul, Aditi, Nitish

---

## 🧠 Contributions & Improvements

- Replicated SE(3)-equivariant diffusion pipeline
- Integrated evaluation with ProteinMPNN + OmegaFold
- Planned extensions for conditional and sequence-aware structure generation

---

## 📄 Citation

```
@inproceedings{lin2023genie,
  title={Generating Novel, Designable, and Diverse Protein Structures by Equivariantly Diffusing Oriented Residue Clouds},
  author={Lin, Yeqing and AlQuraishi, Mohammed},
  booktitle={ICML},
  year={2023}
}
```

---


