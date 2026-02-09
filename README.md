[FRENCH VERSION BELOW]

# Sleep Stage Classification - Kaggle 3A CentraleSupélec

This repository contains our solution for the 3rd-year Machine Learning challenge. The objective is to predict sleep stages (including the difficult N1 stage) from physiological signals (EEGs from 8 patients), using a Machine Learning-based approach.

## Project contents

Here are the key elements you will find in this repository:

* **`notebook.ipynb`**: The final notebook submitted for evaluation. It contains the entire pipeline (dataset creation, pre-processing, LOSO training, prediction).
* **`report.pdf`**: A concise report explaining the theoretical foundations and our methodological choices.
* **`debug_plot_analysis/`**: Folder containing 8 visual comparisons between the actual hypnogram and our predictions over a full night.
* **Error analysis**:
* `PCA_2D.png`: 2D PCA visualization to illustrate class separability.
* `confusion_matrix_LOSO.png`: Confusion matrix from our cross-validation (Leave-One-Subject-Out).
    * `mispredictions_N1.json`: File specifically listing errors at stage N1 (the most difficult part of the challenge).
    * `optimal_weights.json`: The optimal class weights used to counteract imbalance.

## Installation and Environment

This project uses **uv** for fast and reproducible dependency management.

1.  **Clone the repository:**
```bash
git clone [https://github.com/TOUJAN-Oceam/Kaggle_ML_3A_CentraleSupelec.git](https://github.com/TOUJAN-Oceam/Kaggle_ML_3A_CentraleSupelec.git)
  cd Kaggle_ML_3A_CentraleSupelec
```

2.  **Install dependencies:**
```bash
uv sync
```

3.  **Launch the notebook or scripts:**
```bash
uv run jupyter notebook
# or
uv run python script.py
```

## Technical Methodology

Our approach is based on the following libraries (see `pyproject.toml`):

* **Signal Processing** (`scipy.signal`): Filtering (Butterworth), spectral analysis (Welch, Spectrograms) to extract frequency bands (Alpha, Beta, Delta, etc.).
* **Feature Engineering**: Calculation of temporal statistics (Skewness, Kurtosis, Entropy, IQR) on signal windows.
* **Modeling**: Use of **XGBoost** with class weighting (`class_weight`).
* **Validation**: **LOSO (Leave-One-Subject-Out)** and `GroupKFold` strategy to avoid data leakage between segments from the same patient.

## Key Results

* **Main difficulty**: Distinguishing stage N1 (often confused with wakefulness or N2). See `mispredictions_N1.json` and `confusion_matrix_LOSO.png` for details.

* **Performance**: Metric evaluated: F1 score, 80 participants
Public score: 0.81320  (top 5 leaderboard)
Private Score: 0.76992 (final result, top 10 leaderboard)


[FRENCH VERSION]


# Classification de Stades de Sommeil - Kaggle 3A CentraleSupélec

Ce dépôt contient notre solution pour le challenge de Machine Learning de 3ème année. L'objectif est de prédire les stades de sommeil (dont le difficile stade N1) à partir de signaux physiologiques (EEG de 8 patients), en utilisant une approche basée sur le Machine Learning.

## Contenu du projet

Voici les éléments clés que vous trouverez dans ce dépôt :

* **`notebook.ipynb`** : Le notebook final soumis pour l'évaluation. Il contient tout le pipeline (création de dataset, pré-processing, entraînement LOSO, prédiction).
* **`report.pdf`** : Un rapport concis expliquant les fondements théoriques et nos choix méthodologiques.
* **`debug_plot_analysis/`** : Dossier contenant 8 comparaisons visuelles entre l'hypnogramme réel et nos prédictions sur une nuit complète.
* **Analyse d'erreurs** :
    * `PCA_2D.png` : Visualisation PCA en 2D pour illustrer la séparabilité des classes.
    * `confusion_matrix_LOSO.png` : Matrice de confusion issue de notre validation croisée (Leave-One-Subject-Out).
    * `mispredictions_N1.json` : Fichier listant spécifiquement les erreurs sur le stade N1 (le point dur du challenge).
    * `optimal_weights.json` : Les poids de classes optimaux utilisés pour contrer le déséquilibre.

## Installation et Environnement

Ce projet utilise **uv** pour une gestion des dépendances rapide et reproductible.

1.  **Cloner le dépôt :**
    ```bash
    git clone [https://github.com/TOUJAN-Oceam/Kaggle_ML_3A_CentraleSupelec.git](https://github.com/TOUJAN-Oceam/Kaggle_ML_3A_CentraleSupelec.git)
    cd Kaggle_ML_3A_CentraleSupelec
    ```

2.  **Installer les dépendances :**
    ```bash
    uv sync
    ```

3.  **Lancer le notebook ou les scripts :**
    ```bash
    uv run jupyter notebook
    # ou
    uv run python script.py
    ```

## Méthodologie Technique

Notre approche s'appuie sur les bibliothèques suivantes (voir `pyproject.toml`) :

* **Traitement du Signal** (`scipy.signal`) : Filtrage (Butterworth), analyse spectrale (Welch, Spectrogrammes) pour extraire les bandes de fréquences (Alpha, Beta, Delta, etc.).
* **Feature Engineering** : Calcul de statistiques temporelles (Skewness, Kurtosis, Entropy, IQR) sur les fenêtres de signal.
* **Modélisation** : Utilisation de **XGBoost** avec pondération des classes (`class_weight`).
* **Validation** : Stratégie de **LOSO (Leave-One-Subject-Out)** et `GroupKFold` pour éviter le data leakage entre les segments d'un même patient.

## Résultats Clés

* **Difficulté principale** : La distinction du stade N1 (souvent confondu avec l'éveil ou N2). Voir `mispredictions_N1.json` et `confusion_matrix_LOSO.png` pour le détail.

* **Performance** : Metrique évaluée : F1 score, 80 participants
Public score: 0.81320  (top 5 leaderboard)
Private Score: 0.76992 (résultat final, top 10 du leaderboard)


---
*Auteurs : [TOUJAN_Océam] & [BAUTISTA-Ivan]*
