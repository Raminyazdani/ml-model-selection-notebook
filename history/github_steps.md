# Git History Reconstruction: ML Model Selection Notebook (Expanded Edition)

This document reconstructs a believable development history for the ML Model Selection & Evaluation Toolkit project. Each step represents a logical development milestone showing how a developer would build this project incrementally.

---

## History Expansion Note

**Previous run:** N_old = 8 steps
**Current run:** N_new = 13 steps
**Multiplier achieved:** 13/8 = 1.625× (exceeds minimum requirement of 1.5×)

### Old Steps → New Steps Mapping

| Old Steps | New Steps | Expansion Strategy |
|-----------|-----------|-------------------|
| Old step 01 (Initial setup) | New steps 01-02 | Split: Separate README creation from requirements/gitignore |
| Old step 02 (K-fold CV) | New steps 03-04 | Split: Separate data generation from CV implementation |
| Old step 03 (Classification) | New steps 05-07 | Split + Oops/Hotfix: Step 05 introduces wrong import, step 06 fixes it, step 07 adds evaluation |
| Old step 04 (Decision boundaries) | New step 08 | Kept as single step |
| Old step 05 (Ridge/Lasso) | New steps 09-10 | Split: Separate Ridge regression from Lasso regression |
| Old step 06 (Polynomial/Spline) | New steps 11-12 | Split: Separate polynomial from spline + add assignment reference |
| Old step 07 (Assignment reference) | [Merged into step 12] | Consolidated with spline regression |
| Old step 08 (Portfolio polish) | New step 13 | Kept as final polish step |

### Oops → Hotfix Sequence (Steps 05-06)

**What broke:** In step 05, I introduced a typo in the import statement for scikit-learn's discriminant analysis module. Instead of importing from `sklearn.discriminant_analysis`, I incorrectly used `sklearn.discriminant`.

**How I noticed:** When testing the classification models, Python raised an `ImportError: No module named 'sklearn.discriminant'`. The correct module is `sklearn.discriminant_analysis`.

**What fixed it:** In step 06, I corrected the import path from:
```python
from sklearn.discriminant import LinearDiscriminantAnalysis, QuadraticDiscriminantAnalysis
```
to:
```python
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis, QuadraticDiscriminantAnalysis
```

This is a realistic mistake that can happen when working from memory with sklearn's nested module structure.

---

## Overview

The project was developed over 13 commits, starting from repository initialization and progressively adding machine learning techniques for model selection and evaluation. The development follows a natural progression from simple to complex techniques.

---

## Step 01: Initial commit with README

**Commit Message**: `Initial commit: Add basic README`

**Description**:
Start the repository with a basic README describing the project goals and setup instructions.

**Files Added**:
- `README.md` - Basic project description with setup instructions

**Rationale**:
Every good repository starts with a README to communicate project purpose and basic usage.

**Snapshot**: `history/steps/step_01/`

---

## Step 02: Add requirements and gitignore

**Commit Message**: `Add requirements.txt and .gitignore`

**Description**:
Add dependency management with requirements.txt and configure .gitignore for Python/Jupyter development.

**Files Added**:
- `requirements.txt` - Core ML dependencies (numpy, matplotlib, jupyter, scikit-learn)
- `.gitignore` - Python, Jupyter, IDE, and OS ignore patterns

**Rationale**:
Essential project infrastructure for reproducibility and clean version control.

**Snapshot**: `history/steps/step_02/`

---

## Step 03: Create notebook with data generation

**Commit Message**: `Start notebook with synthetic data generation`

**Description**:
Initialize the Jupyter notebook with title, introduction, and synthetic dataset generation using scikit-learn's `make_circles`.

**Files Added/Modified**:
- `ml_model_selection_analysis.ipynb` - Created with cells 0-6
  - Project title and overview
  - Import statements
  - Synthetic data generation with `make_circles`
  - Dataset visualization

**Key Features**:
- Synthetic circular dataset creation
- Basic plotting and visualization setup
- Foundation for classification tasks

**Rationale**:
Start with data generation before implementing any ML algorithms. Visualization helps understand the data structure.

**Snapshot**: `history/steps/step_03/`

---

## Step 04: Implement K-fold cross-validation

**Commit Message**: `Add custom K-fold cross-validation implementation`

**Description**:
Implement K-fold cross-validation from scratch to understand the fundamental concept of model evaluation.

**Files Modified**:
- `ml_model_selection_analysis.ipynb` - Extended to cells 0-9
  - Custom K-fold CV function
  - Train/test splitting logic
  - Accuracy and F1 score computation
  - Test with sample model

**Key Features**:
- Manual K-fold implementation (not using sklearn's)
- Educational approach showing the algorithm step-by-step
- Reusable function for later model evaluation

**Rationale**:
Understanding cross-validation by building it from scratch is more educational than using a black-box library function.

**Snapshot**: `history/steps/step_04/`

---

## Step 05: Add classification models (OOPS: wrong import)

**Commit Message**: `Add classification models for comparison`

**Description**:
Set up three classification algorithms for comparison, but accidentally use the wrong import path for discriminant analysis models.

**Files Modified**:
- `ml_model_selection_analysis.ipynb` - Extended to cells 0-11
  - Model fitting section header
  - Import statements (WITH ERROR)
  - Model instantiation for Logistic Regression, LDA, QDA

**Bug Introduced**:
```python
from sklearn.discriminant import LinearDiscriminantAnalysis, QuadraticDiscriminantAnalysis
```
Should be `sklearn.discriminant_analysis`, not `sklearn.discriminant`.

**Rationale**:
This is a realistic mistake - sklearn's module structure can be confusing, and it's easy to misremember the correct path.

**Snapshot**: `history/steps/step_05/`

---

## Step 06: Fix import path for discriminant analysis

**Commit Message**: `Fix: Correct sklearn import path for discriminant analysis`

**Description**:
Fix the import error from the previous commit. The correct module is `sklearn.discriminant_analysis`.

**Files Modified**:
- `ml_model_selection_analysis.ipynb` - Fixed cell 11
  - Corrected import path
  - All three models now properly instantiated

**Bug Fixed**:
```python
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis, QuadraticDiscriminantAnalysis
```

**Rationale**:
Quick hotfix after testing revealed the import error. Models can now be used successfully.

**Snapshot**: `history/steps/step_06/`

---

## Step 07: Add model evaluation with varying K values

**Commit Message**: `Evaluate models across different K-fold values`

**Description**:
Systematically evaluate all three classification models using different K values (5, 10, 15, 20, 25, 30) to analyze performance stability.

**Files Modified**:
- `ml_model_selection_analysis.ipynb` - Extended to cells 0-14
  - K-values evaluation section
  - Loop through different K values
  - Performance tracking and visualization
  - Comparison plots

**Key Features**:
- Multiple K values tested: 5, 10, 15, 20, 25, 30
- Performance metrics collection
- Visual comparison of model stability
- Analysis of optimal K value

**Rationale**:
Shows how different K values affect cross-validation results and demonstrates model performance stability.

**Snapshot**: `history/steps/step_07/`

---

## Step 08: Add decision boundary visualization

**Commit Message**: `Add decision boundary visualization for classifiers`

**Description**:
Implement comprehensive decision boundary plots to visualize how each model separates classes in 2D space.

**Files Modified**:
- `ml_model_selection_analysis.ipynb` - Extended to cells 0-21
  - Decision boundary plotting utility
  - Side-by-side visualizations for all models
  - Analysis of linear vs. quadratic boundaries
  - Discussion of model suitability for circular data

**Key Features**:
- Visual decision boundaries with color-coded regions
- Training data overlay
- Clear comparison of Logistic Regression, LDA, and QDA
- Explanation of why QDA works better for non-linear data

**Rationale**:
Visualization helps understand model behavior beyond just accuracy metrics. Makes it clear why QDA outperforms linear models on circular data.

**Snapshot**: `history/steps/step_08/`

---

## Step 09: Implement Ridge regression

**Commit Message**: `Add Ridge regression with regularization`

**Description**:
Extend the project to regression tasks by implementing Ridge (L2) regression with hyperparameter tuning.

**Files Modified**:
- `ml_model_selection_analysis.ipynb` - Extended to cells 0-24
  - Synthetic regression data generation
  - Ridge regression implementation
  - Lambda (alpha) parameter tuning via cross-validation
  - MSE evaluation

**Key Features**:
- L2 regularization
- Hyperparameter search across multiple lambda values
- Cross-validation for model selection
- Regularization path visualization

**Rationale**:
Ridge regression demonstrates how regularization prevents overfitting and shows practical hyperparameter tuning.

**Snapshot**: `history/steps/step_09/`

---

## Step 10: Implement Lasso regression

**Commit Message**: `Add Lasso regression for feature selection`

**Description**:
Implement Lasso (L1) regression to complement Ridge and demonstrate feature selection capabilities.

**Files Modified**:
- `ml_model_selection_analysis.ipynb` - Extended to cells 0-30
  - Lasso regression implementation
  - Alpha parameter tuning
  - Comparison with Ridge regression
  - Optimal model selection and test evaluation

**Key Features**:
- L1 regularization with sparsity
- Feature selection properties
- Side-by-side comparison with Ridge
- Best model evaluation on test set

**Rationale**:
Lasso complements Ridge by offering feature selection through L1 regularization, showing the trade-offs between different regularization methods.

**Snapshot**: `history/steps/step_10/`

---

## Step 11: Add polynomial regression

**Commit Message**: `Implement polynomial regression for non-linear patterns`

**Description**:
Move beyond linear models by implementing polynomial regression with various degrees.

**Files Modified**:
- `ml_model_selection_analysis.ipynb` - Extended to cells 0-32
  - Polynomial feature transformation
  - Polynomial regression with degrees 2, 4, 5, 6
  - Visualization of polynomial fits
  - Analysis of overfitting vs. underfitting

**Key Features**:
- Polynomial feature generation
- Multiple complexity levels
- Visual comparison of different polynomial degrees
- Discussion of model complexity trade-offs

**Rationale**:
Demonstrates "beyond linearity" techniques and the bias-variance trade-off through polynomial regression.

**Snapshot**: `history/steps/step_11/`

---

## Step 12: Add spline regression and assignment reference

**Commit Message**: `Add spline regression and include assignment reference`

**Description**:
Complete the non-linear techniques with spline regression and add the original assignment notebook for reference.

**Files Modified/Added**:
- `ml_model_selection_analysis.ipynb` - Extended to cells 0-36 (complete analysis)
  - Spline transformer implementation
  - Spline regression with varying knots (2, 3, 4, 10) and degrees (2, 3, 10)
  - Complex model exploration
  - Complete analysis notebook
- `assignment_3_handout.ipynb` - Original assignment file added for reference

**Key Features**:
- Spline regression with B-splines
- Multiple knot configurations
- Flexible non-linear modeling
- Original assignment preserved for context

**Rationale**:
Splines provide flexible non-linear regression and complete the "beyond linearity" section. Including the original assignment maintains transparency about educational origins.

**Snapshot**: `history/steps/step_12/`

---

## Step 13: Final portfolio polish

**Commit Message**: `Final: Portfolio polish and professional documentation`

**Description**:
Transform the project into portfolio-ready state by enhancing README, removing assignment traces, and adding professional documentation.

**Files Modified/Added**:
- `README.md` - Complete rewrite with 13 professional sections:
  - Clear overview and problem statement
  - Detailed tech stack
  - Comprehensive setup instructions
  - Data inputs/outputs documentation
  - Key features list
  - Reproducibility notes
  - Troubleshooting section
  - Project background

- `ml_model_selection_analysis.ipynb` - Cleaned of assignment traces:
  - Removed "Task X:" prefixes from markdown cells
  - Removed "Lecture" references
  - Removed TODO comments from code cells
  - Preserved all analysis and implementations

- `project_identity.md` - New professional documentation:
  - Project identity and branding
  - Display title and tagline
  - Problem statement and approach
  - Stack and keywords
  - Inputs and outputs

**Key Changes**:
- All assignment language removed
- README transformed from basic to portfolio-grade
- Professional framing throughout
- Complete technique documentation
- Educational context preserved in separate file

**Rationale**:
Final polish transforms the educational exercise into a professional portfolio piece that showcases ML engineering skills.

**Snapshot**: `history/steps/step_13/` (matches final repository state)

---

## Development Timeline Summary

| Step | Focus | Key Addition | Cells | Files |
|------|-------|--------------|-------|-------|
| 01 | Setup | README | - | 1 |
| 02 | Infrastructure | requirements, .gitignore | - | 3 |
| 03 | Data | Synthetic data generation | 0-6 | 4 |
| 04 | CV | K-fold cross-validation | 7-9 | 4 |
| 05 | Models (Oops) | Classification models (wrong import) | 10-11 | 4 |
| 06 | Hotfix | Fixed import path | 10-11 | 4 |
| 07 | Evaluation | K-values comparison | 12-14 | 4 |
| 08 | Visualization | Decision boundaries | 15-21 | 4 |
| 09 | Regression | Ridge regression | 22-24 | 4 |
| 10 | Regression | Lasso regression | 25-30 | 4 |
| 11 | Non-linear | Polynomial regression | 31-32 | 4 |
| 12 | Non-linear | Spline regression + assignment | 33-36 | 5 |
| 13 | Polish | Portfolio documentation | 0-36 | 6 |

---

## Verification

✓ Final snapshot (step_13) matches current repository state exactly:
- .gitignore
- README.md
- requirements.txt
- ml_model_selection_analysis.ipynb
- assignment_3_handout.ipynb
- project_identity.md

All snapshots exclude:
- `.git/` directory
- `history/` directory (no recursion)
- tracking files (report.md, suggestion.txt, suggestions_done.txt)

---

## Expansion Techniques Used

### Strategy A: Split Large Commits
- **Step 01-02**: Split initial setup into README first, then requirements/gitignore
- **Step 03-04**: Split data generation from CV implementation
- **Step 07**: Split model evaluation into separate step from model setup
- **Step 09-10**: Split Ridge and Lasso into separate commits
- **Step 11-12**: Split polynomial and spline regression

### Strategy B: Oops → Hotfix Sequence
- **Step 05**: Introduced realistic import path typo (`sklearn.discriminant` instead of `sklearn.discriminant_analysis`)
- **Step 06**: Immediately fixed the import error

Both strategies create a realistic development narrative that shows:
1. Incremental progress (not doing everything at once)
2. Real-world mistakes and fixes (import errors are common)
3. Logical grouping of related changes
4. Professional development practices

---

## How to Use

Each `history/steps/step_XX/` directory contains a complete snapshot at that development stage. To explore:

```bash
cd history/steps/step_XX/
# View files as they existed at that commit
jupyter notebook ml_model_selection_analysis.ipynb  # For steps 03+
```

This reconstruction demonstrates:
- Incremental development methodology
- Logical progression from simple to complex
- Realistic mistakes and debugging
- Professional code organization
- Documentation evolution
- Transformation from coursework to portfolio
