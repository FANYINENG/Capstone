# Black Box Optimization Capstone Project

This repository contains the documentation, datasets, and sequential optimization models developed for a multi-dimensional black box optimization problem featuring 8 unique target functions. Over a 10-round query timeline, Bayesian optimization and advanced search algorithms were deployed to efficiently discover global optima.

---

## 📁 Repository Structure

The project is organized into the following components:

### 1. `notebooks/` (Function Notebooks)
This directory contains 8 individual Jupyter notebooks—one dedicated to each black box function. Each notebook serves as a complete, self-contained record of the optimization lifecycle for that function and includes:
* **The Data:** Historical evaluation points and search space constraints.
* **Submitted Queries:** The exact batches of coordinate queries generated and evaluated for each sequential round.
* **The Models:** The specific Gaussian Process surrogates or alternative models configured during each iteration.

### 2. `datasheet.md`
A comprehensive markdown document detailing the underlying data asset. It answers critical tracking questions regarding the data's composition, the exact query generation strategies utilized, preprocessing/scaling transformations applied, and guidelines for proper data distribution and maintenance.

### 3. `model_card.md`
A structured document outlining the machine learning and optimization strategy used across the 10 rounds of the project. It provides an overview of the technical approach, details regarding the strategic evolution of the acquisition functions, an optimization performance summary across all 8 functions, underlying assumptions, and ethical considerations for deployment.
