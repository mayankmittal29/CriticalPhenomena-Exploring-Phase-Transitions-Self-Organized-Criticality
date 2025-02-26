# 🌌 CriticalPhenomena: Exploring Phase Transitions & Self-Organized Criticality 🌌

[![Python Version](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![NumPy](https://img.shields.io/badge/NumPy-1.20+-green.svg)](https://numpy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.4+-orange.svg)](https://matplotlib.org/)

A computational physics project exploring critical phenomena through percolation theory and the Bak-Tang-Wiesenfeld sandpile model.

## 🔍 Overview

This repository contains simulations of critical phenomena in statistical physics, focusing on:
- 2D percolation theory and cluster size distributions
- 1D percolation probability and cluster statistics
- Self-organized criticality in the sandpile model

The code demonstrates how complex systems exhibit phase transitions, power laws, and self-organization at critical points.

## 📊 Questions

### Q1: 2D Percolation and Cluster Size Distribution

#### 📝 Explanation:

- The code simulates a 2D lattice and computes the cluster size distribution for different probabilities p.
- At pc​, the distribution follows a power law, indicating the emergence of a spanning cluster.
- The log-log plot shows how the distribution changes from subcritical (p=0.3) to supercritical (p=0.7) regimes.
  
#### 🧮 Cluster Size Distribution:

- The lattice is generated with probability pc​, and clusters are identified using the label function from scipy.ndimage.
- The cluster sizes are counted using np.bincount.

#### 📈 Power-Law Fit:

- The power-law function ns=a⋅s−τ is fitted to the data using curve_fit from scipy.optimize.
- The critical exponent τ is extracted from the fit.

#### 📊 Plot:

- The log-log plot shows the cluster size distribution (data points) and the fitted power-law curve.
- The slope of the fitted curve corresponds to the critical exponent τ.

#### 🔬 Explanation of What is Happening

- **Subcritical Regime (p<pc​):**
  - Clusters are small and isolated.
  - The cluster size distribution decays exponentially, meaning there are very few large clusters.

- **Critical Regime (p=pc​):**
  - A spanning cluster (percolating cluster) emerges.
  - The cluster size distribution follows a power law ns∼s−τ, indicating scale-free behavior.
  - The critical exponent τ characterizes the distribution of cluster sizes at this point.

- **Supercritical Regime (p>pc​):**
  - The spanning cluster dominates the system.
  - The cluster size distribution deviates from the power law, as most sites belong to the giant cluster.

#### 🧠 Inference:

- At pc​, the distribution is scale-free, confirming the critical point.
- The exponent can be estimated from the slope of the log-log plot at pc​.

---

### Q2: 1D Percolation Analysis

#### 📝 Explanation of the Code

- **Percolation Probability in 1D:**
  - In 1D, the percolation probability Π(p;L) is given by:
  - Π(p;L)=p^L
  - This formula is used to compute the probability of having a spanning cluster (all sites occupied) in a 1D lattice of size L.

- **Cluster Size Distribution in 1D:**
  - The 1D lattice is generated as a binary array where each site is occupied with probability p.
  - Clusters are identified as contiguous sequences of 1s (occupied sites).
  - The size of each cluster is recorded, and the distribution of cluster sizes is computed using np.bincount.

- **Plotting:**
  - The percolation probability Π(p;L) is plotted as a function of p for different lattice sizes L.
  - The cluster size distribution ns​ vs s is plotted on a log-log scale for p=0.5 and p=0.9.

#### 🧠 Inference

- **Percolation Probability:**
  - In 1D, the critical probability pc=1. This means that an infinite cluster (spanning cluster) only forms when p=1.
  - The plot of Π(p;L) shows that the probability of percolation increases sharply as p approaches 1.

- **Cluster Size Distribution:**
  - For p<1, the cluster size distribution decays exponentially, meaning large clusters are rare.
  - The log-log plot shows that the number of clusters decreases rapidly as the cluster size increases, confirming the absence of a power-law distribution in 1D.

#### 🔑 Key Observations

- In 1D, percolation is trivial because a spanning cluster can only exist if all sites are occupied (p=1).
- The cluster size distribution does not exhibit a power-law behavior, unlike in 2D, where a power-law distribution emerges at the critical point pc​.

---

### Q3: Sandpile Model - Self-Organized Criticality

#### 📝 Code Summary: 

- Imports required libraries (numpy, matplotlib, animation) for simulations and visualization.
- Defines constants (L = 70, threshold = 7) based on the roll number for grid size and toppling limit.
- Creates a sandpile lattice of size 70x70, where each cell initially holds 7+1 grains.
- Runs stabilization by redistributing grains from unstable cells (> 7) to neighbors until equilibrium.
- Stores each step of the stabilization process as frames for animation.
- Perturbs the stable sandpile by adding grains at the center (L//2, L//2) and repeats the stabilization process.
- Plots animations showing the sandpile dynamics before and after perturbation.
- Saves two GIFs: one for initial stabilization and another for perturbation effects.
- Plots snapshots at t=0, t=10, and t=20 to visualize how grains spread over time.
- Demonstrates self-organized criticality, where small perturbations cause large-scale avalanches.

#### 🔍 Explanation of the Four Figures in Detail
##### 1. Initial Configuration (Before Any Toppling)

- **What it shows:**
   - A uniform grid of 70x70, where every cell contains exactly 7+1 grains.
   - The color represents the grain count, with darker shades indicating higher values.
   - No toppling has occurred yet.

- **Why it matters:**
   - This is the starting point before any redistribution happens.
   - It helps in understanding how the system evolves from an unstable state.

##### 2. Final Stable Configuration (After Toppling Ends)

- **What it shows:**
  - The lattice after stabilization, where no cell contains 7 or more grains.
  - Uneven distribution emerges as grains have spread outward due to toppling.
  - Some regions have lower values, while others retain more grains.

- **Why it matters:**
  - Demonstrates how the system naturally organizes itself into a stable pattern.
  - Reveals the avalanche effect, where grains cascade to neighboring cells.

##### 3. Perturbation at t = 0 (Grains Added at the Center)

- **What it shows:**
  - After reaching equilibrium, additional grains are added at the center (L//2, L//2).
  - The surrounding cells remain unchanged at this step.
  - The center is now overloaded, making it unstable.

- **Why it matters:**
  - This is the trigger event that causes a chain reaction.
  - Shows how a small disturbance can lead to self-organized criticality.

##### 4. Perturbation Response at t = 10 and t = 20

- **What it shows:**
  - At t = 10, grains start spreading outward as toppling begins.
  - At t = 20, the avalanche has propagated further, covering a wider area.
  - Eventually, the system reaches a new stable configuration.

- **Why it matters:**
  - Helps visualize how disturbances propagate in complex systems.
  - This behavior is seen in earthquakes, landslides, and financial markets.

#### 🧠 Conclusion

- The figures illustrate self-organized criticality, where small changes can trigger large-scale effects.
- The model explains how nature balances systems, from sandpiles to power grids and stock markets.

> **Note:** The repository includes animated GIFs for both the initial stabilization process and the system's response after perturbation!

## 🛠️ Technologies Used

- **Python** - Core programming language
- **NumPy** - For efficient numerical computations
- **Matplotlib** - For data visualization and animations
- **SciPy** - For scientific computing functions

## ⚡ Installation

```bash
git clone https://github.com/yourusername/CriticalPhenomena.git
cd CriticalPhenomena
```

## 📚 References

- Stauffer, D., & Aharony, A. (1994). Introduction to Percolation Theory. CRC Press.
- Bak, P., Tang, C., & Wiesenfeld, K. (1987). Self-organized criticality: An explanation of the 1/f noise. Physical Review Letters, 59(4), 381-384.
- Newman, M. E. J. (2005). Power laws, Pareto distributions and Zipf's law. Contemporary Physics, 46(5), 323-351.
