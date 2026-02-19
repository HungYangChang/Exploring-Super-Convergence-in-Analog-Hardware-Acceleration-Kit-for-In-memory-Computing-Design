# Exploring Super-Convergence in Analog Hardware Acceleration for In-memory Computing

![Python](https://img.shields.io/badge/python-3.6%2B-blue)
![License](https://img.shields.io/badge/license-MIT-blue)
![Stars](https://img.shields.io/github/stars/HungYangChang/Exploring-Super-Convergence-in-Analog-Hardware-Acceleration-Kit-for-In-memory-Computing-Design)

> Combining super-convergence training with analog in-memory computing to dramatically accelerate neural network training while reducing energy consumption.

**[Full Report (PDF)](552_Final_project.pdf)** · **[Poster (PDF)](Poster.pdf)** · **[Main Notebook](ECSE552_Project.ipynb)**

---

## Problem

Training large DNNs is computationally intensive and the Von Neumann bottleneck — constant data transfer between memory and compute — prevents energy-efficient training. Even with analog in-memory computing, training still requires many epochs and significant time.

## Solution

We propose a hardware-software co-optimization approach: combining **super-convergence** (a learning rate policy that achieves the same accuracy in far fewer epochs) with **analog in-memory computing** (IBM's AIHWKit) to achieve faster training on energy-efficient hardware.

## Architecture

```
┌─────────────────────────────────────────────────────┐
│       Hardware-Software Co-Optimization             │
├─────────────────────────────────────────────────────┤
│                                                     │
│   ┌─────────────────────────────────────────────┐   │
│   │  Software: Super-Convergence Policy         │   │
│   │  • 1-cycle learning rate schedule           │   │
│   │  • Fewer epochs to convergence              │   │
│   │  • Cyclical momentum                        │   │
│   └──────────────────┬──────────────────────────┘   │
│                      │                              │
│                      ▼                              │
│   ┌─────────────────────────────────────────────┐   │
│   │  Hardware: Analog RPU Simulation            │   │
│   │  • IBM AIHWKit                              │   │
│   │  • In-memory weight storage                 │   │
│   │  • Eliminates Von Neumann bottleneck        │   │
│   └──────────────────┬──────────────────────────┘   │
│                      │                              │
│                      ▼                              │
│            Faster, more efficient training           │
│                                                     │
└─────────────────────────────────────────────────────┘
```

### Key Design Decisions

- **Super-convergence + analog hardware:** First exploration of combining these two techniques for compound training speedup.
- **Dual-framework comparison:** Implemented both in PyTorch (baseline) and IBM AIHWKit (analog) to isolate hardware vs. software contributions.

## Stack

| Layer | Technology |
|-------|-----------|
| Framework | IBM AIHWKit, PyTorch |
| Compute | Google Colab (GPU with CUDA) |
| Algorithm | Super-convergence (1-cycle LR policy) |
| Language | Python 3.6+ |

## Getting Started

```bash
# Option 1: Run on Google Colab (recommended)
# Upload ECSE552_Project.ipynb to Colab, select GPU runtime

# Option 2: Build AIHWKit from source (for CUDA support)
# See aihwkit_installation.ipynb for detailed instructions

# Option 3: PyTorch-only baseline
# Run super_convergence.ipynb for the software-only comparison
```

### Notebooks

| Notebook | Purpose |
|----------|---------|
| `ECSE552_Project.ipynb` | Full analog training with super-convergence |
| `super_convergence.ipynb` | PyTorch-only super-convergence vs. normal training |
| `aihwkit_installation.ipynb` | Build IBM AIHWKit from source with CUDA |

## Results

| Metric | Normal Training | Super-Convergence | Improvement |
|--------|:-:|:-:|:-:|
| Epochs to converge | Many | Fewer | Significant reduction |
| Training time | Baseline | Reduced | Compound speedup with analog HW |
| Energy efficiency | Digital baseline | Analog + SC | Orders of magnitude potential |

## Known Limitations

- Evaluated on standard benchmarks; production-scale validation is future work.
- AIHWKit simulation approximates real analog behavior but doesn't capture all physical non-idealities.
- Super-convergence benefits vary by architecture and dataset.

## Related Publications

> **PipeBERT: High-throughput BERT Inference for ARM Big.LITTLE Multi-core Processors**
> _Journal of Signal Processing Systems (IEEE SiPS 2022)_
> H.-Y. Chang et al.

> **AI Hardware Acceleration with Analog Memory**
> _IBM Journal of Research and Development_
> H.-Y. Chang, G.W. Burr et al.

## License

MIT — see [LICENSE](./LICENSE) for details.

---

Built by [Hung-Yang (James) Chang](https://github.com/HungYangChang) · McGill University
