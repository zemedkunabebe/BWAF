# BWAF-Net: A Prior-Guided Attention Framework for Multi-Modal Data Fusion in Computational Genomics

This repository contains the complete source code, datasets, and experimental notebooks for the paper: *"BWAF-Net: A Prior-Guided Attention Framework for Multi-Modal Data Fusion in Computational Genomics"*.

The project introduces **BWAF-Net**, a novel multi-modal deep learning framework that accurately identifies human gene promoter regions. Our key finding is the identification and solution for "Modality Collapse," a common failure mode in multi-modal architectures. BWAF-Net uses a novel **knowledge-as-a-controller** fusion mechanism where biological priors explicitly gate information flow from deep encoders, leading to a significant performance increase over standard fusion methods.

### Key Features

*   **Multi-Modal Architecture:** Integrates a Transformer for DNA sequence grammar and a Graph Attention Network (GAT) for gene regulatory context.
*   **Novel Fusion Mechanism:** Implements a **Biologically Weighted Attention Fusion (BWAF)** layer that uses explicit biological priors (motif counts) to dynamically guide the fusion process, overcoming Modality Collapse.
*   **Rigorous Benchmark:** All experiments are performed on a challenging benchmark using a strict chromosome-holdout split and dinucleotide-shuffled negative controls to prevent data leakage and test for true grammatical understanding.
*   **Fully Reproducible Workflow:** Includes all code for data generation, model training, ablation studies, and interpretability analysis to ensure the entire research process is transparent.

### Repository Structure

```
.
├── LICENSE
├── README.md
├── Final_Aligned_Dataset.csv    # Pre-processed dataset for training
├── graph_data.pt                # Pre-processed graph data for the GAT
│
├── Data Exploration, Feture Extraction and Preprocessing/
│   ├── Genome Data Exploration.ipynb
│   ├── Genome Feture Extraction.ipynb
│   ├── GAT Data Exploration.ipynb
│   └── GAT Data Preprocessing.ipynb
│
├── BWAF-Net-train.ipynb                 # Notebook to train the main BWAF-Net model
├── baseline_cross_attention.ipynb     # Notebook to train the cross-attention baseline
├── ablation_training.ipynb              # Notebook to train all ablation models
├── interpretability.ipynb               # Notebook for XAI on the final BWAF-Net model
├── interpret_all_ablations.ipynb        # Notebook for comparative bias analysis
│
└── results/ (contains all generated outputs)
    ├── results_bwaf/
    ├── results_fusion_baselines/
    ├── results_ablation_final2/
    ├── results_xai/
    └── results_xai_ablation/
```

### Setup and Installation

#### 1. Create a Virtual Environment

It is highly recommended to use a virtual environment (like `venv` or `conda`) to manage dependencies.

```bash
# Create and activate a virtual environment
python3 -m venv bwaf_env
source bwaf_env/bin/activate  # On Windows use: bwaf_env\Scripts\activate
```

#### 2. Create `requirements.txt` and Install Dependencies

The necessary packages are listed in the paper. For easy installation, create a `requirements.txt` file with the following content:

**`requirements.txt`:**
```
numpy<2.0
pandas
matplotlib
seaborn
scikit-learn
scipy
tqdm
notebook
ipykernel
torch
torchvision
torchaudio
torch_geometric
shap
```

Now, install all packages from the file:
```bash
pip install -r requirements.txt
```
**Note:** For GPU support, please follow the official installation instructions for PyTorch and PyTorch Geometric for your specific CUDA version.

### How to Reproduce Results

You can reproduce our results using two paths: a quick path using pre-processed data, or a full path that regenerates everything from scratch.

#### Path A: Quick Reproduction (Recommended)

This path uses the provided pre-processed data to train the models and generate all results.

1.  **Train the Main BWAF-Net Model:**
    *   Run the `BWAF-Net-train.ipynb` notebook. This will train the model and save the best checkpoint.

2.  **Train Baselines and Ablation Models:**
    *   Run `baseline_cross_attention.ipynb` to train the SOTA fusion baseline.
    *   Run `ablation_training.ipynb` to train all five ablation models.

3.  **Generate Interpretability Figures:**
    *   Run `interpretability.ipynb` to analyze the trained BWAF-Net model.
    *   Run `interpret_all_ablations.ipynb` to generate the comparative bias analysis plots.

#### Path B: Full Data Regeneration (Optional)

This path regenerates the `Final_Aligned_Dataset.csv` and `graph_data.pt` files from raw public data. This is not required to verify the main results.

1.  **Download Raw Data:** Follow the download instructions in the `Genome Data Exploration.ipynb` and `GAT Data Exploration.ipynb` notebooks to fetch the required genome, annotation, and network files.
2.  **Run Preprocessing Notebooks:** Execute the notebooks in the `Data Exploration, Feture Extraction and Preprocessing/` directory in order to regenerate the final dataset files.
3.  **Follow Path A:** Once the data files are regenerated, follow the steps in "Path A" to train the models.

### Citation

If you use this work, please cite our paper:

> Zemedkun Abebe Debela and Adane Mamuye. (2025). *BWAF-Net: A Prior-Guided Attention Framework for Multi-Modal Data Fusion in Computational Genomics*. IEEE/ACM Transactions on Computational Biology and Bioinformatics.
>
> *(A BibTeX entry will be provided upon publication.)*
