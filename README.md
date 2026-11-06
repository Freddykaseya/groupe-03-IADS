# Credit Card Fraud Detection

Projet académique du groupe 03 consacré à la détection des transactions frauduleuses par carte bancaire à l'aide d'algorithmes de machine learning.

## Question de recherche

Dans quelle mesure les modèles de régression logistique, Random Forest et Isolation Forest permettent-ils de détecter efficacement les transactions frauduleuses sur un jeu de données fortement déséquilibré ?

## Objectifs

- Préparer et explorer le jeu de données.
- Entraîner et comparer trois modèles : Logistic Regression, Random Forest et Isolation Forest.
- Évaluer leur capacité à identifier les transactions frauduleuses, en tenant compte du déséquilibre des classes.

## Données

Le projet utilise le jeu de données **Credit Card Fraud Detection** disponible sur Kaggle :  
https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

Consulter [DATA.md](DATA.md) pour les informations relatives aux données, à leur téléchargement et à leur préparation.

## Méthodologie et évaluation

Les modèles seront comparés à l'aide des métriques suivantes :

- Precision
- Recall
- F1-score
- PR-AUC (aire sous la courbe précision-rappel)

## Organisation du dépôt

- `notebooks/` : notebooks Colab/Jupyter pour l'exploration, la préparation, l'entraînement et l'évaluation.
- `paper/` : fiche projet, article scientifique et documents de recherche.
- `slides/` : présentation du projet.

## Équipe — Groupe 03

- Fanny Mawussé
- Freddy Kaseya
- Rydwane Ichola

## Environnement

Python, pandas, NumPy, scikit-learn, matplotlib et Jupyter/Google Colab.
