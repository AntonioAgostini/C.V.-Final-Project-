# Joint Detection of AI-Generated Images and Post-Processing Alterations in Real-World Scenarios

**Authors:**  
| name| matrix |
|---|---|
| Antonio Agostini | 1995653 |
| Giorgia Saolini | 1933076 |

---

**Colab Notebook:**  
[Open the project notebook on Google Colab](https://colab.research.google.com/drive/1IpTRFOgMdlx_t3OaMaVKaViSCQnwWTrx#scrollTo=i6JIlAvFFG-P)

---

## Project Goal
This project addresses the problem of robust AI-generated image detection in realistic conditions, where images are often altered by post-processing operations such as internet transmission or re-digitization.
The goal is to train a unified multi-task model that simultaneously solves two forensic tasks:

1. **Real/Fake classification**: determine whether an image is a real photograph or AI-generated.
2. **Transformation classification**: identify which post-processing operation has been applied to the image (`original`, `internet-transmitted`, `re-digitized`).

The main idea is to study whether joint training can improve robustness compared to training two separate unimodal models.

---

## Dataset
The project uses **RRDataset**, a real-world robustness benchmark containing both real and AI-generated images across three transformation conditions: `original`, `internet-transmitted`, and `re-digitized`.
Because of hardware constraints, a balanced subset of the dataset can be selected, as allowed by the project guidelines.

---

## Method
The proposed architecture is based on:

- a **shared backbone** for feature extraction;
- two independent classification heads:
  - one for the binary real/fake task,
  - one for the transformation classification task.

The model is trained with a **weighted sum of two cross-entropy losses**:

\[
L_{total} = \alpha \cdot L_{RF} + \beta \cdot L_{Trans}
\]

where the weights are used to study the trade-off between the two tasks and to perform ablation experiments.

---

## Experimental Setup
The project follows a standard deep learning pipeline in **PyTorch**, as required by the course guidelines.

The code is organized into the following sections:

- `Imports`
- `Globals`
- `Utils`
- `Data`
- `Network`
- `Train`
- `Evaluation`

Training is performed on a fixed train/validation/test split, with reproducible seeds and balanced sampling where needed. The evaluation includes accuracy and F1-score for both tasks, plus a detailed analysis by transformation type.

---

## Baselines
The project was also compared against two unimodal baselines, one for real/fake detection and one for transformation classification.
This comparison was carried out to assess whether the multi-task model could improve robustness or, instead, introduce task interference between the two objectives.
These baselines were not implemented as part of the Colab code, but were trained and evaluated separately. 
Their results are reported in the presentation through a histogram plot, which is also included in the project images.

---

## Results Analysis
The experimental analysis focuses on three aspects:

- overall performance of the unimodal and multi-task models;
- performance breakdown by transformation type;
- effect of different loss weights in the ablation study.
- effect of different amount of data for train/val/test and data augmentation.

This allows us to understand which post-processing operations are most harmful to detection and whether real and AI-generated images react differently to the same transformation.

---

## Reproducibility
To ensure reproducibility, the project includes:

- fixed random seeds;
- a clearly defined environment;
- saved checkpoints;
- logged hyperparameters and metrics;
- deterministic train/validation/test splits.

---

## Requirements
The project is implemented in **Python** using **PyTorch**, following the mandatory framework specified by the course.

Example dependencies include:

- `torch`
- `torchvision`
- `numpy`
- `pandas`
- `scikit-learn`
- `matplotlib`
- `tqdm`

---

## How to Run
1. Open the notebook on Google Colab.
2. Install the required dependencies.
3. Download or link the RRDataset subset.
4. Run the training cells.
5. Run evaluation to obtain the final metrics and plots.

---

## Presentation
You can click [here](https://LINK_DELLA_PRESENTAZIONE) to read the presentation.
The project is intended to be presented in a **10-minute oral presentation**, following the course structure:

- Title
- Outline
- Problem Statement
- State of the Art
- Proposed Method
- Dataset
- Experimental Setup
- Model Evaluation
- Conclusions
- References

---

## Notes
This project is a hands-on computer vision project, not a survey. The focus is on methodology, reproducibility, and experimental analysis, with a small but meaningful novelty in the training strategy.
