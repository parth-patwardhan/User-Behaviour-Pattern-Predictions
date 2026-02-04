# User Behaviour Pattern Prediction using Graph Neural Networks

[![Python 3.6+](https://img.shields.io/badge/python-3.6+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-1.0+-red.svg)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Deep Learning](https://img.shields.io/badge/Deep%20Learning-GNN-green.svg)](https://github.com)

## Overview

This project implements state-of-the-art **Graph Neural Network (GNN)** architectures for predicting user behaviour patterns in temporal interaction networks. We replace the traditional JODIE model with advanced GNN-based approaches including **Graph Attention Networks (GAT)** and **Temporal Graph Networks (TGN)** to achieve better performance in dynamic embedding learning and link prediction tasks.

### Key Features

- **Multiple GNN Architectures**: Implementation of GAT, GCN, and TGN models
- **Temporal Dynamics**: Handles time-evolving graphs for realistic user-item interaction modeling
- **Comprehensive Evaluation**: Includes Recall@K, Mean Reciprocal Rank (MRR), and AUC metrics
- **Hyperparameter Optimization**: Grid search implementation for optimal model configuration
- **Real-world Datasets**: Experiments on Wikipedia, Reddit, and Last.fm datasets
- **Comparative Analysis**: Baseline comparison with JODIE model

## Table of Contents

- [Architecture](#architecture)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Datasets](#datasets)
- [Models](#models)
- [Usage](#usage)
- [Experiments](#experiments)
- [Results](#results)
- [Project Structure](#project-structure)
- [Contributors](#contributors)
- [Citation](#citation)
- [License](#license)

## Architecture

The project explores three main approaches:

1. **Graph Attention Networks (GAT)**: Multi-head attention mechanism for learning node representations
2. **Temporal Graph Networks (TGN)**: Memory-augmented GNN for temporal interaction prediction
3. **JODIE Baseline**: Dynamic embedding model for comparison

### Why GNNs over JODIE?

- Better representation learning through graph structure
- Improved temporal dependency modeling
- Enhanced generalization on unseen nodes
- Scalability to large-scale interaction networks

## Installation

### Prerequisites

- Python 3.6 or higher
- CUDA-capable GPU (recommended for large datasets)
- 8GB+ RAM

### Setup

```bash
# Clone the repository
git clone https://github.com/your-username/User-Behaviour-Pattern-Prediction.git
cd User-Behaviour-Pattern-Prediction

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies for GAT/TGN
pip install torch torchvision torchaudio
pip install torch-geometric
pip install pandas numpy scikit-learn tqdm matplotlib seaborn

# For JODIE baseline (separate requirements)
cd Jodie
pip install -r requirements.txt
cd ..
```

## Quick Start

### 1. Download Datasets

```bash
# Download Wikipedia dataset
wget http://snap.stanford.edu/jodie/wikipedia.csv -P data/

# Download Reddit dataset
wget http://snap.stanford.edu/jodie/reddit.csv -P data/

# Or use the provided notebooks which include download commands
```

### 2. Preprocess Data for TGN

```bash
# Convert to dense npy format for TGN
python temporal_graph_network/utils/preprocess_data.py --data wikipedia --bipartite
```

### 3. Train Models

#### Train GAT Model

```bash
# Run the GAT implementation notebook
jupyter notebook GAT_Implementation.ipynb
```

#### Train TGN Model

```bash
# Self-supervised learning with link prediction
python temporal_graph_network/link_prediction.py \
    --data wikipedia \
    --use_memory \
    --prefix tgn-attn \
    --n_runs 10 \
    --n_epoch 50 \
    --bs 200 \
    --n_degree 10
```

#### Train JODIE Baseline

```bash
cd Jodie
python jodie.py --network wikipedia --model jodie --epochs 50
cd ..
```

## Datasets

| Dataset | Nodes | Edges | Features | Time Span | Domain |
|---------|-------|-------|----------|-----------|--------|
| Wikipedia | 9,227 | 157,474 | 172 | 1 month | User-article edits |
| Reddit | 10,984 | 672,447 | 172 | 1 month | User-subreddit posts |
| Last.fm | 1,980 | 1,293,103 | 172 | ~2 years | User-artist listening |

### Data Format

Each dataset contains interactions with the following structure:
```
user_id, item_id, timestamp, state_label, comma_separated_list_of_features
```

## Models

### 1. Graph Attention Networks (GAT)

Implementation highlights:
- Multi-head attention mechanism (8-16 heads)
- 3-layer architecture with dropout regularization
- Negative sampling for link prediction
- Class-weighted loss for imbalanced data

**Key Parameters:**
- Hidden dimensions: 128
- Attention heads: 8
- Dropout: 0.3
- Learning rate: 0.0005

### 2. Temporal Graph Networks (TGN)

Implementation highlights:
- Memory module for node state tracking
- Temporal attention layers
- Self-supervised link prediction
- Inductive learning capability

**Key Parameters:**
- Memory dimension: 172
- Node dimension: 100
- Time dimension: 100
- Message dimension: 100

### 3. JODIE (Baseline)

Original dynamic embedding model for temporal networks:
- RNN-based embedding updates
- State change prediction
- T-batch processing

## Usage

### Running Experiments

#### 1. GAT with Hyperparameter Tuning

The `GAT_Implementation.ipynb` notebook includes grid search over:
- Hidden dimensions: [16, 32]
- Attention heads: [8, 16]
- Learning rates: [0.01, 0.001]
- Dropout rates: [0.3, 0.5]
- Weight decay: [0.0, 0.001]

#### 2. Reddit Dataset Experiments

```bash
# Run the Reddit dataset notebook
jupyter notebook LASTFM_Datset_Test_1.ipynb
```

#### 3. Custom Dataset

To use your own dataset:

1. Format data as CSV with columns: `user_id`, `item_id`, `timestamp`, `state_label`, `comma_separated_list_of_features`
2. Place in `data/` directory
3. Update data path in notebooks or scripts
4. Run preprocessing and training

## Experiments

### Experiment 1: GAT on Wikipedia

**File**: `GAT_Implementation.ipynb`

- Hyperparameter optimization via grid search
- Evaluation metrics: Recall@10, MRR
- Comparative analysis of different configurations

### Experiment 2: GCN on Reddit

**File**: `LASTFM_Datset_Test_1.ipynb`

- Link prediction on large-scale Reddit dataset
- Node feature engineering
- Training/validation split analysis

### Experiment 3: Temporal GCN-GRU

**File**: `Test_2.ipynb`

- Combines GCN with GRU for temporal modeling
- Rating prediction task
- Electronics dataset experiments

## Results

### Performance Comparison

| Model | Dataset | Recall@10 | MRR | AUC |
|-------|---------|-----------|-----|-----|
| GAT | Wikipedia | 1.0000 | 0.7750 | - |
| GAT | Reddit | 1.0000 | 0.7453 | - |
| TGN | Wikipedia | - | - | 0.98+ |
| JODIE | Wikipedia | - | - | 0.95+ |

### Key Findings

- GAT achieves perfect recall on test sets with proper hyperparameter tuning
- Multi-head attention (8+ heads) significantly improves performance
- Temporal models (TGN) outperform static approaches
- Memory-augmented architectures show better inductive capabilities

## Project Structure

```
User-Behaviour-Pattern-Prediction/
├── README.md
├── LICENSE
├── requirements.txt
│
├── data/                          # Dataset directory
│   └── dummy.txt
│
├── notebooks/
│   ├── GAT_Implementation.ipynb      # GAT experiments
│   ├── LASTFM_Datset_Test_1.ipynb   # Reddit dataset
│   └── Test_2.ipynb                  # Temporal GCN-GRU
│
├── temporal_graph_network/           # TGN implementation
│   ├── link_prediction.py           # Main training script
│   ├── net/
│   │   └── tgn.py                   # TGN model
│   ├── modules/
│   │   ├── memory.py                # Memory module
│   │   ├── temporal_attention.py    # Temporal attention
│   │   ├── message_aggregator.py
│   │   └── embedding_module.py
│   └── utils/
│       ├── preprocess_data.py       # Data preprocessing
│       ├── data_processing.py
│       └── utils.py
│
├── Jodie/                            # JODIE baseline
│   ├── jodie.py                     # Main JODIE script
│   ├── library_models.py            # Model definitions
│   ├── library_data.py              # Data utilities
│   ├── tbatch.py                    # T-batch algorithm
│   ├── requirements.txt
│   └── README.md
│
└── docs/
    ├── AI_Lab_report.pdf            # Technical report
    └── AI_Lab_Presentation.pdf      # Presentation slides
```

## Contributors

- **Parth Patwardhan** - [GitHub](https://github.com/parth-patwardhan)
- **Muhammed Rizwan** - [GitHub](https://github.com/muhammed-rizwan)

## Citation

If you use this code in your research, please cite:

```bibtex
@misc{user-behaviour-gnn-2025,
  author = {Patwardhan, Parth and Rizwan, Muhammed},
  title = {User Behaviour Pattern Prediction using Graph Neural Networks},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/your-username/User-Behaviour-Pattern-Prediction}
}
```

### Related Papers

- **TGN**: Rossi, E., Chamberlain, B., Frasca, F., et al. (2020). "Temporal Graph Networks for Deep Learning on Dynamic Graphs"
- **GAT**: Veličković, P., Cucurull, G., Casanova, A., et al. (2018). "Graph Attention Networks"
- **JODIE**: Kumar, S., Zhang, X., Leskovec, J. (2019). "Predicting Dynamic Embedding Trajectory in Temporal Interaction Networks"

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- JODIE implementation based on [claws-lab/jodie](https://github.com/claws-lab/jodie)
- TGN implementation inspired by [twitter-research/tgn](https://github.com/twitter-research/tgn)
- Datasets from [SNAP Stanford](http://snap.stanford.edu/jodie/)

---

**Made with PyTorch and PyTorch Geometric**

For questions or issues, please open an issue on GitHub.
