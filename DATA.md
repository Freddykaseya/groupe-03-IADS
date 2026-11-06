# Documentation des données

## Jeu de données

- **Nom :** Credit Card Fraud Detection
- **Source :** Kaggle — https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
- **Fichier attendu :** `creditcard.csv`
- **Taille documentée :** 284 807 transactions
- **Transactions frauduleuses :** 492
- **Variable cible :** `Class` (1 = fraude, 0 = transaction normale)

## Téléchargement

Télécharger le jeu de données depuis la page Kaggle ci-dessus, puis placer le fichier `creditcard.csv` dans l'environnement de travail (Google Colab ou Jupyter).

Ne pas déposer le fichier CSV dans le dépôt GitHub sans vérifier les conditions de licence, la taille du fichier et les règles de partage applicables.

## Préparation prévue

1. Charger le fichier CSV avec pandas.
2. Vérifier les dimensions, types, valeurs manquantes et doublons.
3. Examiner la distribution de la variable `Class`.
4. Séparer les variables explicatives et la cible.
5. Construire un découpage entraînement/test en conservant la proportion des classes lorsque cela est approprié.
6. Appliquer toute opération de mise à l'échelle ou de rééquilibrage uniquement sur les données d'entraînement afin d'éviter les fuites de données.

## Licence et conditions d'utilisation

La licence doit être vérifiée directement sur la page Kaggle du jeu de données avant toute redistribution ou publication des données. Ne pas supposer une licence qui n'est pas explicitement indiquée.
