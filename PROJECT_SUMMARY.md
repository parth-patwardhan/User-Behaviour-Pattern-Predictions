# Project Summary: User Behaviour Pattern Prediction

## 🎯 Project Overview

**Type:** Deep Learning Research Project
**Domain:** Graph Neural Networks, Temporal Network Analysis
**Task:** User Behaviour Pattern Prediction in Temporal Interaction Networks
**Implementation:** PyTorch, PyTorch Geometric

## 🏗️ Architecture Implementations

### 1. Graph Attention Networks (GAT)
- **File:** `GAT_Implementation.ipynb`
- **Features:**
  - Multi-head attention mechanism (8-16 heads)
  - 3-layer deep architecture
  - Hyperparameter grid search optimization
  - Negative sampling for link prediction

- **Results:**
  - Recall@10: 1.0000 (Wikipedia & Reddit)
  - MRR: 0.7750 (Wikipedia), 0.7453 (Reddit)

### 2. Temporal Graph Networks (TGN)
- **Location:** `temporal_graph_network/`
- **Features:**
  - Memory-augmented graph neural network
  - Temporal attention layers
  - Self-supervised link prediction
  - Inductive learning capability

- **Components:**
  - Memory module for node states
  - Message passing framework
  - Temporal encoding
  - Neighbor sampling

### 3. JODIE Baseline
- **Location:** `Jodie/`
- **Purpose:** Baseline comparison
- **Method:** RNN-based dynamic embeddings
- **Features:**
  - T-batch algorithm
  - State change prediction
  - Interaction prediction

## 📊 Datasets

| Dataset | Size | Description | Use Case |
|---------|------|-------------|----------|
| **Wikipedia** | 534 MB | User-article edits over 1 month | Primary evaluation |
| **Reddit** | 2.2 GB | User-subreddit posts over 1 month | Scalability testing |
| **Last.fm** | - | User-artist listening history | Long-term patterns |

## 🔬 Experiments Conducted

### Experiment 1: GAT Hyperparameter Optimization
- **Goal:** Find optimal GAT configuration
- **Method:** Grid search over 32 combinations
- **Parameters tuned:**
  - Hidden dimensions: [16, 32]
  - Attention heads: [8, 16]
  - Learning rates: [0.01, 0.001]
  - Dropout: [0.3, 0.5]
  - Weight decay: [0.0, 0.001]

### Experiment 2: Large-Scale Link Prediction
- **Dataset:** Reddit (672K+ edges)
- **Task:** Predict future user-item interactions
- **Approach:** GCN with edge features

### Experiment 3: Temporal Modeling
- **Model:** GCN-GRU hybrid
- **Dataset:** Electronics ratings
- **Task:** Rating prediction with temporal dynamics

## 📈 Key Achievements

✅ **Perfect Recall:** Achieved 100% Recall@10 on test sets
✅ **High MRR:** 0.77+ Mean Reciprocal Rank
✅ **Scalability:** Successfully handled 2.2GB datasets
✅ **Reproducibility:** Complete setup documentation
✅ **Optimization:** Comprehensive hyperparameter tuning

## 🛠️ Technical Stack

```
Core:
- Python 3.6+
- PyTorch 1.7+
- PyTorch Geometric 2.0+

Data Processing:
- NumPy, Pandas
- Scikit-learn

Visualization:
- Matplotlib, Seaborn

Development:
- Jupyter Notebooks
- Git version control
```

## 📁 Repository Structure

```
📦 User-Behaviour-Pattern-Prediction
│
├── 📄 README.md                    # Main documentation (comprehensive)
├── 📄 SETUP_GUIDE.md              # Installation & running guide
├── 📄 GIT_SETUP.md                # Git instructions (detailed)
├── 📄 QUICK_START_COMMANDS.md     # Copy-paste Git commands
├── 📄 PROJECT_SUMMARY.md          # This file
├── 📄 requirements.txt             # Python dependencies
├── 📄 .gitignore                   # Git ignore rules
├── 📄 LICENSE                      # MIT License
│
├── 📓 GAT_Implementation.ipynb     # GAT experiments
├── 📓 LASTFM_Datset_Test_1.ipynb  # Reddit dataset
├── 📓 Test_2.ipynb                 # Temporal GCN-GRU
│
├── 📂 temporal_graph_network/      # TGN implementation
│   ├── link_prediction.py         # Training script
│   ├── 📂 net/                     # Model definitions
│   ├── 📂 modules/                 # GNN modules
│   └── 📂 utils/                   # Utilities
│
├── 📂 Jodie/                       # JODIE baseline
│   ├── jodie.py                   # Main script
│   ├── library_models.py          # Models
│   └── requirements.txt            # Dependencies
│
├── 📂 data/                        # Data directory
│   └── dummy.txt                  # Placeholder
│
└── 📂 docs/                        # Documentation
    ├── AI_Lab_report.pdf          # Technical report
    └── AI_Lab_Presentation.pdf    # Slides
```

## 🎓 Academic Context

**Course:** AI Lab / Deep Learning Lab
**Topic:** Graph Neural Networks for Temporal Interaction Networks
**Objective:** Compare modern GNN approaches with baseline models

## 💡 Key Contributions

1. **Implementation Comparison:**
   - Side-by-side comparison of GAT, TGN, and JODIE
   - Performance benchmarking on multiple datasets

2. **Hyperparameter Analysis:**
   - Systematic grid search
   - Performance vs. parameter trade-offs documented

3. **Scalability Demonstration:**
   - Handling datasets from 534MB to 2.2GB
   - Memory-efficient implementations

4. **Reproducibility:**
   - Complete setup instructions
   - All dependencies documented
   - Clear execution steps

## 🚀 How to Use This Project

### For Learning:
1. Start with `GAT_Implementation.ipynb` to understand GAT
2. Read the technical report in `docs/`
3. Explore TGN implementation for advanced concepts

### For Research:
1. Use as baseline for temporal graph learning
2. Extend models with new features
3. Compare with your own approaches

### For Demonstration:
1. Share GitHub repository link
2. Reference in resume/portfolio
3. Cite in academic work

## 📚 Learning Outcomes

From this project, you've demonstrated expertise in:

- ✅ Graph Neural Networks (GNN)
- ✅ Attention Mechanisms (Multi-head attention)
- ✅ Temporal Network Analysis
- ✅ Link Prediction Tasks
- ✅ PyTorch & PyTorch Geometric
- ✅ Hyperparameter Optimization
- ✅ Large-scale Data Processing
- ✅ Model Evaluation & Metrics
- ✅ Scientific Documentation
- ✅ Software Engineering (Git, documentation)

## 🎯 Future Enhancements (Ideas)

1. **Model Improvements:**
   - Implement GraphSAGE for comparison
   - Add heterogeneous graph support
   - Try different aggregation methods

2. **Experiments:**
   - Cross-dataset generalization
   - Few-shot learning scenarios
   - Real-time prediction evaluation

3. **Engineering:**
   - Add unit tests
   - Implement CI/CD pipeline
   - Create interactive visualization dashboard

4. **Documentation:**
   - Add architecture diagrams
   - Create video tutorials
   - Write blog post explaining the work

## 🌟 Standout Features

What makes this repository impressive:

1. ✨ **Multiple Implementations:** Not just one model, but 3 different approaches
2. ✨ **Real Datasets:** Using standard benchmark datasets from Stanford SNAP
3. ✨ **Comprehensive Docs:** README, setup guides, Git instructions
4. ✨ **Reproducible:** Anyone can run your experiments
5. ✨ **Professional:** Badges, structure, clean code
6. ✨ **Academic Rigor:** Includes report and presentation

## 📞 Contact & Contribution

**Contributors:**
- Parth Patwardhan
- Muhammed Rizwan

**Contributions Welcome:**
- Bug reports via GitHub Issues
- Feature requests
- Pull requests for improvements
- Documentation enhancements

## 📖 Citation

```bibtex
@misc{user-behaviour-gnn-2025,
  author = {Patwardhan, Parth and Rizwan, Muhammed},
  title = {User Behaviour Pattern Prediction using Graph Neural Networks},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/YOUR-USERNAME/User-Behaviour-Pattern-Prediction}
}
```

## 🏆 Achievement Summary

This project demonstrates:
- Advanced deep learning skills
- Research methodology
- Software engineering best practices
- Documentation excellence
- Academic rigor
- Practical implementation ability

---

**Ready to showcase to the world! 🚀**

**Your repository stands out because it's:**
- ✅ Complete
- ✅ Well-documented
- ✅ Reproducible
- ✅ Professional
- ✅ Comprehensive
