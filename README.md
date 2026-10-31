# PathMNIST Classification

A University of Sydney COMP5318 course team project comparing **PCA + RBF SVM, MLP and CNN** on a course-provided, nine-class colorectal histology image dataset.

## My contribution
Chen Shi: data exploration and preprocessing, the PCA + RBF SVM approach and its hyperparameter search. MLP/CNN work and the combined comparison are team contributions. The notebook contains the integrated team deliverable.

## Evaluation design
- Course-provided training set: 32,000 RGB images (28 × 28 × 3).
- Fixed stratified split for development: 25,600 fitting / 6,400 validation images, seed 42.
- Validation macro-F1 is the model-selection metric.
- PCA is fitted on fitting data only during tuning; nine SVM C/gamma combinations are compared.
- Final selected models are refitted on all 32,000 training images and scored on the held-out 8,000-image test set.
- The notebook preserves saved search results, classification reports, confusion matrices and the final model comparison.

## View results
Open [the notebook](pathmnist_classification.ipynb) on GitHub to inspect the saved results without executing training.

## Reproduce
Python 3.13 was used for the saved verified outputs; package compatibility can vary by platform. Create a fresh environment and install the recorded dependencies:

```bash
python3.13 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python -m jupyter lab
```

Place the four course arrays in [Assignment2Data](Assignment2Data/README.md), open `pathmnist_classification.ipynb`, and run all cells in order. To reproduce only the final selected models, run Setup, Section 1 and Section 4. Full hyperparameter searches can take substantial CPU time.

**Data limitation:** the large course arrays are not uploaded. The original MedMNIST split is different and cannot reproduce these exact saved scores. Readers without the authorised course arrays can still inspect the complete saved outputs. See the dataset folder's README for file shapes and source information.

## Interpretation and attribution
The images do not include patient/slide identifiers, so the patch-level stratified split does not establish patient-independent generalisation. This is a teaching experiment, not a clinically validated diagnostic system.

Course team project, Group 36. Student identifiers are omitted from this portfolio copy. The original notebook's AI acknowledgement, references and shared-contribution context are retained. PathMNIST/MedMNIST attribution is provided in the notebook. No new license is asserted over course or team materials.
