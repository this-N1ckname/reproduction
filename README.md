# TSP: heuristics and neural approaches (reproduction)

This notebook explores classical and learning-based methods for the Euclidean Traveling Salesman Problem (TSP). Inspired by recent neural approaches, the focus is on comparing simple heuristics with compact models under limited compute.

## Methods

* Greedy (nearest neighbor)
* Christofides
* Greedy + 2-opt
* Multi-start + 2-opt (custom)
* Heatmap GNN (edge prediction + greedy decoding)
* Autoregressive model (REINFORCE + sampling)

## Key observations (implementation insights)

* **2-opt is essential** — gives the largest consistent improvement over greedy.
* **Multi-start > smarter model** — restarting greedy often beats more complex methods.
* **Decoding matters as much as the model** — poor tour construction ruins good predictions.
* **Masking is critical (AR model)** — without strict masking, the policy collapses.
* **Best-of-N sampling works** — simple trick that significantly improves AR results.
* **Heatmap models are unstable** — require post-processing (2-opt) to be competitive.
* **Scaling is hard** — methods that work at N=20 degrade quickly at larger sizes.

## Notes on reproduction

Instead of reproducing a specific architecture, the notebook explores alternative approaches in the same setting. The main takeaway is that strong heuristics + lightweight improvements remain highly competitive, especially under compute constraints.
