# Quick Setup Guide

## Initial Setup

### 1. Environment Setup

```bash
# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install all dependencies
pip install -r requirements.txt
```

### 2. Download Datasets

```bash
# Create data directory if not exists
mkdir -p data

# Download Wikipedia dataset (534 MB)
wget http://snap.stanford.edu/jodie/wikipedia.csv -P data/

# Download Reddit dataset (2.2 GB)
wget http://snap.stanford.edu/jodie/reddit.csv -P data/

# Alternatively, run the notebooks which include download commands
```

### 3. Verify Installation

```bash
# Test PyTorch installation
python -c "import torch; print(f'PyTorch {torch.__version__}')"

# Test PyTorch Geometric
python -c "import torch_geometric; print(f'PyG {torch_geometric.__version__}')"

# Check CUDA availability (for GPU support)
python -c "import torch; print(f'CUDA available: {torch.cuda.is_available()}')"
```

## Running Experiments

### Quick Test - GAT Implementation

```bash
# Launch Jupyter
jupyter notebook

# Open GAT_Implementation.ipynb
# Run all cells to see GAT in action
```

### Full Training Pipeline

#### Option 1: Graph Attention Networks (GAT)

```bash
# Open Jupyter notebook
jupyter notebook GAT_Implementation.ipynb

# The notebook includes:
# - Data loading and preprocessing
# - Hyperparameter grid search
# - Model training and evaluation
# - Performance metrics (Recall@10, MRR)
```

#### Option 2: Temporal Graph Networks (TGN)

```bash
# Preprocess data first
python temporal_graph_network/utils/preprocess_data.py --data wikipedia --bipartite

# Train TGN model
python temporal_graph_network/link_prediction.py \
    --data wikipedia \
    --use_memory \
    --prefix tgn-attn \
    --n_runs 1 \
    --n_epoch 50 \
    --batch 200 \
    --n_degree 10 \
    --lr 0.0001

# For multiple runs (to get average performance)
python temporal_graph_network/link_prediction.py \
    --data wikipedia \
    --use_memory \
    --prefix tgn-attn \
    --n_runs 10 \
    --n_epoch 50
```

#### Option 3: JODIE Baseline

```bash
cd Jodie

# Install JODIE-specific dependencies
pip install -r requirements.txt

# Download data (if not already done)
bash download_data.sh

# Train JODIE
python jodie.py --network wikipedia --model jodie --epochs 50

# Evaluate
python evaluate_interaction_prediction.py --network wikipedia --model jodie --epoch 49

cd ..
```

## Understanding the Outputs

### GAT Outputs
- Training loss progression
- Test accuracy and recall
- MRR (Mean Reciprocal Rank)
- Best hyperparameter configuration

### TGN Outputs
- Saved models in `saved_models/`
- Checkpoints in `saved_checkpoints/`
- Results in `results/` (pickle files)
- Logs in `log/`

### JODIE Outputs
- Model checkpoints in `Jodie/saved_models/`
- Validation/test results printed to console
- State change prediction metrics

## Troubleshooting

### Common Issues

#### CUDA Out of Memory
```bash
# Reduce batch size
python temporal_graph_network/link_prediction.py --batch 100  # instead of 200
```

#### Import Errors
```bash
# Reinstall PyTorch Geometric
pip install torch-geometric --force-reinstall
```

#### Download Issues
```bash
# Use curl instead of wget
curl http://snap.stanford.edu/jodie/wikipedia.csv -o data/wikipedia.csv
```

## Performance Benchmarks

Expected training times (on GPU):

| Model | Dataset | GPU | Training Time | Memory |
|-------|---------|-----|---------------|--------|
| GAT | Wikipedia | RTX 3080 | ~5 minutes | ~2GB |
| TGN | Wikipedia | RTX 3080 | ~20 minutes | ~4GB |
| JODIE | Wikipedia | RTX 3080 | ~30 minutes | ~3GB |
| GAT | Reddit | RTX 3080 | ~15 minutes | ~6GB |

## Next Steps

1. Run the baseline experiments in the notebooks
2. Modify hyperparameters in the code
3. Try different datasets
4. Compare model performances
5. Visualize results

## Getting Help

- Check the main [README.md](README.md) for detailed documentation
- Review the [AI_Lab_report.pdf](AI_Lab_report.pdf) for technical details
- Open an issue on GitHub for bugs or questions
