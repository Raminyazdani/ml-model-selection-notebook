# ML Model Selection & Evaluation Toolkit

A comprehensive Jupyter notebook demonstrating machine learning model selection, cross-validation, and evaluation techniques from linear to non-linear models.

**Stack:** Python, Jupyter Notebook, scikit-learn, NumPy, Matplotlib

## Overview

This project showcases fundamental machine learning model selection and evaluation workflows. It demonstrates practical implementation of cross-validation, model comparison, regularization techniques, and visualization of decision boundaries for both classification and regression tasks.

## Problem & Approach

**Problem:** How do you systematically select and evaluate machine learning models for different types of data and tasks? How do you ensure your models generalize well to unseen data?

**Approach:**
- **Generalization**: Implement K-fold cross-validation from scratch to assess model performance
- **Model Selection**: Compare multiple classification algorithms (Logistic Regression, LDA, QDA) with decision boundary visualization
- **Regularization**: Apply Ridge and Lasso regression to prevent overfitting
- **Non-linearity**: Explore polynomial and spline regression for complex patterns

## Tech Stack

- **Python 3.x** - Core programming language
- **Jupyter Notebook** - Interactive development environment
- **scikit-learn** - Machine learning models and utilities
- **NumPy** - Numerical computations
- **Matplotlib** - Data visualization

## Repository Structure

```
ml-model-selection-notebook/
├── ml_model_selection_analysis.ipynb  # Main analysis notebook (portfolio version)
├── assignment_3_handout.ipynb         # Original educational version (reference)
├── requirements.txt                   # Python dependencies
└── README.md                          # This file
```

## Setup / Installation

**Install dependencies:**
```bash
pip install -r requirements.txt
```

Or install packages individually:
```bash
pip install numpy matplotlib jupyter scikit-learn
```

**Requirements:**
- Python 3.7 or higher
- Jupyter Notebook or JupyterLab

## How to Run

1. **Clone or navigate to the repository:**
```bash
cd ml-model-selection-notebook
```

2. **Launch Jupyter:**
```bash
jupyter notebook ml_model_selection_analysis.ipynb
```

Or for the original educational version:
```bash
jupyter notebook assignment_3_handout.ipynb
```

3. **Execute cells** sequentially from top to bottom using Shift+Enter

## Data / Inputs

**Inputs:**
- Synthetic datasets generated programmatically using scikit-learn utilities:
  - `make_circles()` for classification tasks
  - Generated regression data for regularization examples
- Configurable parameters for dataset generation (sample size, noise level)
- User-defined hyperparameters (k-folds, regularization strength, polynomial degree)

**Data Location:** All data is self-contained and generated within the notebook - no external data files required.

## Outputs

The notebook produces the following visualizations and metrics:

- **Model Performance Metrics:**
  - Accuracy and F1 scores for classification models
  - Mean Squared Error (MSE) for regression models
  - Cross-validation scores across different k-fold values

- **Visualizations:**
  - Decision boundary plots for classification models
  - Cross-validation performance comparison charts
  - Regularization path plots (Ridge and Lasso)
  - Polynomial and spline regression fit visualizations

- **Output Location:** All results are displayed inline within the notebook cells

## Key Features

1. **Custom K-Fold Cross-Validation Implementation** - Learn how cross-validation works by implementing it from scratch
2. **Model Comparison Framework** - Systematic evaluation of multiple classification algorithms
3. **Hyperparameter Tuning** - Explore the impact of regularization parameters and model complexity
4. **Visual Decision Boundaries** - Understand model behavior through visual representations
5. **Reproducible Experiments** - All analyses use fixed random seeds for consistency

## Reproducibility Notes

- All paths are relative to the project root directory
- Random seeds are set in the notebook for reproducible results
- Self-contained implementation with minimal external dependencies
- Tested with Python 3.7+ and scikit-learn 0.24+

## Troubleshooting

**Import errors:**
```bash
pip install [package-name]
```
Install the specific package that's missing.

**Jupyter not found:**
```bash
pip install jupyter
```

**Notebook-specific issues:**
- Ensure you're running cells sequentially from top to bottom
- Check the first cells for any additional setup instructions
- Restart the kernel if variables seem out of sync (Kernel → Restart & Clear Output)

**Path issues:**
- Ensure you're running Jupyter from the repository root directory
- All data generation happens in-notebook, no external paths needed

## Project Background

This project was originally developed as an educational exercise to demonstrate machine learning fundamentals. It has been refined into a portfolio piece showcasing practical ML engineering skills including model selection, evaluation, and visualization techniques.

## License

This project is available for educational and portfolio purposes.
