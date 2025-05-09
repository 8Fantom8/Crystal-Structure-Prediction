# Crystal-Structure-Prediction
A collection of pipelines and models for extracting structural data from CIF files, visualizing features, and predicting crystallographic properties (space group symmetry and unit cell volume) using machine learning and deep learning approaches.


Project Structure

├── data_preprocessing/           # Scripts and notebooks for parsing CIFs and generating feature CSVs
├── data_augmentation/            # Notebooks for creating augmented structural datasets
├── data_visualization/           # Notebooks for exploratory visualization of features
├── modeling_initial/             # Initial modeling with classical ML algorithms
├── dl_model_1/                   # Deep Learning Model 1: Space group classification (MLP)
├── dl_model_2/                   # Deep Learning Model 2: Advanced MLP classifier
├── dl_model_2_volume/            # Deep Learning Model 2: Volume regression (TabNet)
├── dl_model_3/                   # Deep Learning Model 3: Composition-based symmetry (CRYSPNet-inspired)
├── Models/                       # Saved model weights, organized by model folder
│   ├── model_1/                  # Weights and artifacts from DL Model 1
│   ├── model_2/                  # Weights and artifacts from DL Model 2
│   ├── model_2_volume/           # Weights and artifacts from volume regressor
│   └── model_3/                  # Weights and artifacts from DL Model 3
├── requirements.txt              # Python dependencies
└── README.md                     # This file

Pipeline Overview

Data Preprocessing (data_preprocessing/)

Parse Crystallographic Information Files (CIFs) to generate a CSV of file links and metadata.

Extract primary structural parameters:

Unit cell dimensions: a, b, c

Unit cell angles: α, β, γ

Volume, atomic positions, chemical formula

Compute derived features, e.g., cell anisotropy, axis ratios (b/a, c/a), shape factor

Output: features.csv containing all engineered features

Data Augmentation (data_augmentation/)

Apply transformations to structural descriptors to increase dataset diversity

Techniques may include random lattice distortions, noise injection, and substructure sampling

Output: augmented feature sets for training robust models

Data Visualization (data_visualization/)

Generate histograms, scatter plots, correlation heatmaps, and KDE plots

Explore relationships between features and target variables (space group, volume)

Save interactive visualizations for reporting

Initial Modeling (modeling_initial/)

Train classical ML classifiers (Decision Tree, Random Forest, SVM, etc.) on preprocessed features

Evaluate using cross-validation and hold-out test sets

Output: baseline metrics and confusion matrices

DL Model 1 (dl_model_1/)

A simple MLP classifier for space group prediction

Implemented in PyTorch, with early stopping and dropout

Saves best model weights in Models/model_1/

DL Model 2 (dl_model_2/)

Advanced MLP with residual blocks or attention mechanisms for improved classification

Saves best model weights in Models/model_2/

DL Model 2 (Volume) (dl_model_2_volume/)

Volume regression using TabNet or deep MLP (logged volume target)

Reports RMSE, MAE, and R² on test set

Saves best model weights in Models/model_2_volume/

DL Model 3 (dl_model_3/)

CRYSPNet-inspired dual-head network for composition-based symmetry classification

Uses Matminer descriptors from chemical formulas

Saves best model weights in Models/model_3/
