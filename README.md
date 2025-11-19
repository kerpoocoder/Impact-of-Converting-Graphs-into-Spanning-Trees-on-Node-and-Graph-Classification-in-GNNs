# MSTPrunedGNNs: Minimum Spanning Tree Pruned Graph Neural Networks

[![DOI](https://img.shields.io/badge/DOI-10.1016%2Fj.chemolab.2025.105562-blue)](https://doi.org/10.1016/j.chemolab.2025.105562)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)

Official implementation of the paper **"Impact of converting graphs into spanning trees on node and graph classification in Graph Neural Networks"** published in *Chemometrics and Intelligent Laboratory Systems*.

## 📖 Overview

This repository provides a comprehensive framework for enhancing Graph Neural Networks (GNNs) through Minimum Spanning Tree (MST)-based graph sparsification. Our method leverages theoretical connections between Determinantal Point Processes (DPPs) and spanning trees to significantly reduce graph density while maintaining or improving classification performance.

### Key Contributions

- **Theoretical Foundation**: Establishes connection between DPP edge sampling and minimum spanning trees via transfer-current matrix
- **Efficient Sparsification**: Reduces graph edges by 60-96% while maintaining classification accuracy
- **Multi-Task Framework**: Unified approach for both node classification and graph classification tasks
- **State-of-the-Art Results**: Achieves 98.27% accuracy on AIDS dataset with GIN + LDMST pruning
- **Scalable Implementation**: Modular codebase supporting six GNN architectures and multiple pruning strategies

## 🏗️ Project Structure

```
MSTPrunedGNNs/
├── Node-Classification/          # Node classification framework
│   ├── argument_parser.py       # Command-line argument parsing
│   ├── data_loader.py          # Dataset loading and preprocessing
│   ├── models.py               # GNN model implementations
│   ├── pruners.py              # MST-based pruning strategies
│   ├── trainer.py              # Training loops and optimization
│   ├── evaluator.py            # Performance evaluation metrics
│   ├── main.py                 # Main execution script
│   ├── reporter.py             # Results reporting and visualization
│   ├── requirements.txt        # Python dependencies
│   └── README.md               # Node classification documentation
├── Graph-Classification/       # Graph classification framework  
│   ├── argument_parser.py      # Command-line argument parsing
│   ├── data_loader.py         # Dataset loading and preprocessing
│   ├── models.py              # GNN model implementations
│   ├── pruners.py             # MST-based pruning strategies
│   ├── trainer.py             # Training loops and optimization
│   ├── evaluator.py           # Performance evaluation metrics
│   ├── main.py                # Main execution script
│   ├── reporter.py            # Results reporting and visualization
│   ├── requirements.txt       # Python dependencies
│   └── README.md              # Graph classification documentation
└── README.md                  # This file
```

## 🚀 Quick Start

### Node Classification

```bash
cd Node-Classification
pip install -r requirements.txt
python main.py --dataset Cora --model GCN --prune_type MSTGaussPrune
```

### Graph Classification

```bash
cd Graph-Classification  
pip install -r requirements.txt
python main.py --dataset MUTAG --model GIN --prune_type LDMST
```

## 📊 Supported Features

### Datasets

**Node Classification:**
- Cora, Citeseer, PubMed (Citation networks)
- PPI (Protein-Protein Interaction)

**Graph Classification:**
- MUTAG, AIDS, NCI1 (Chemical compounds)
- PROTEINS (Enzyme classification)
- IMDB-BINARY (Social networks)

### Models
- **GCN**: Graph Convolutional Networks
- **GraphSAGE**: Inductive representation learning
- **GAT**: Graph Attention Networks  
- **GIN**: Graph Isomorphism Networks
- **ChebNet**: Spectral graph convolutions
- **ARMAGNN**: ARMA convolutional filters

### Pruning Strategies
- **NoPrune**: Baseline with original graph
- **MSTGaussPrune**: Gaussian similarity-based MST
- **randomSTPrune**: Random spanning tree pruning
- **LDMST**: Low-degree preference MST
- **HDMST**: High-degree preference MST

## 📈 Key Results

### Node Classification Performance
| Dataset | Original Acc. | Pruned Acc. | Edge Reduction |
|---------|---------------|-------------|----------------|
| Cora    | 88.79%        | 88.82%      | 65.1%          |
| PubMed  | 89.84%        | 89.89%      | 71.2%          |
| PPI     | 91.86%        | 91.93%      | 96.3%          |

### Graph Classification Performance
- **AIDS**: 98.27% accuracy (State-of-the-Art) with GIN + LDMST
- **NCI1**: 77.67% accuracy with GIN + HDMST  
- **PROTEINS**: 72.77% accuracy with GIN + HDMST

## 🔬 Theoretical Foundation

Our approach is grounded in the theoretical connection between:

1. **Determinantal Point Processes (DPPs)** for diverse edge selection
2. **Transfer-current matrix** as the DPP kernel
3. **Minimum Spanning Trees** as efficient approximations of DPP-sampled subgraphs

The method preserves critical structural information while eliminating redundant edges that may act as noise during message passing.

## 📝 Citation

If you use this code or our method in your research, please cite our paper:

```bibtex
@article{taheri2025impact,
  title={Impact of converting graphs into spanning trees on node and graph classification in Graph Neural Networks},
  author={Taheri, Mohammadmahdi and Eftekhari, Mahdi and Aghamollaei, Gholamreza},
  journal={Chemometrics and Intelligent Laboratory Systems},
  volume={105562},
  year={2025},
  publisher={Elsevier},
  doi={10.1016/j.chemolab.2025.105562}
}
```

## 🎯 Search Keywords

- Graph Neural Networks
- Minimum Spanning Tree
- Graph Sparsification
- Node Classification
- Graph Classification
- Determinantal Point Processes
- Transfer-current Matrix
- Effective Resistance
- GNN Pruning
- Graph Reduction
- MST-based GNNs
- Scalable Graph Learning

## 🤝 Contributing

We welcome contributions! Please feel free to submit issues, fork the repository, and create pull requests for any improvements.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Contact

For questions about this implementation or the paper, please contact:
- **Mohammadmahdi Taheri**: [Email](mailto:taheripost@gmail.com)

## 🔗 Links

- **[Paper](https://doi.org/10.1016/j.chemolab.2025.105562)** - Original research paper
- **[Repository](https://github.com/kerpoocoder/MSTPrunedGNNs)** - GitHub repository
- **[Dataset Sources](https://chrsmrrs.github.io/datasets/)** - TUDataset repository

---

*This research was supported by Shahid Bahonar University of Kerman and Mahani Math Center, Afzalipour Research Institute.*