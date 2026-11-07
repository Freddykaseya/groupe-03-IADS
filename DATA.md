# Documentation des données

## 1. Identification et provenance

- **Nom du jeu de données :** Credit Card Fraud Detection
- **Fichier :** `creditcard.csv`
- **Source principale :** Machine Learning Group — Université Libre de Bruxelles (ULB), diffusé sur Kaggle.
- **Page du jeu de données :** https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
- **Période couverte :** transactions effectuées en septembre 2013 sur une période de deux jours par des titulaires de cartes européens.
- **Licence indiquée pour la base de données sur Kaggle :** Open Database License (ODbL). Consulter les conditions de la page Kaggle et le texte de la licence avant toute redistribution. Le dépôt de code du groupe ne redistribue pas le fichier brut.

Le jeu de données est utilisé dans ce projet à des fins académiques pour étudier la détection de transactions frauduleuses dans un contexte de forte rareté de la classe positive.

## 2. Dimensions et description générale

### 2.1 État initial du fichier

Les vérifications effectuées dans Google Colab sur le fichier original donnent :

| Indicateur | Valeur |
|---|---:|
| Nombre de lignes initial | 284 807 |
| Nombre de colonnes | 31 |
| Nombre de variables explicatives | 30 |
| Nombre de variables cibles | 1 |
| Transactions normales (`Class = 0`) | 284 315 |
| Transactions frauduleuses (`Class = 1`) | 492 |
| Part des transactions frauduleuses | 0,172749 % |
| Valeurs manquantes détectées | 0 |
| Valeurs infinies détectées | 0 |
| Occurrences supplémentaires de doublons exacts | 1 081 |
| Groupes distincts de lignes dupliquées | 773 |

**Important :** ces statistiques décrivent le fichier original avant toute suppression de doublons. La décision finale de traitement des doublons sera consignée dans le notebook et reflétée dans les effectifs du jeu de données préparé.

### 2.2 Déséquilibre des classes

La variable cible est fortement déséquilibrée : environ 99,827 % des observations sont des transactions normales et 0,173 % sont frauduleuses. Une stratégie qui prédit systématiquement la classe majoritaire pourrait obtenir une exactitude élevée sans détecter aucune fraude.

Pour cette raison, l'évaluation ne reposera pas uniquement sur l'accuracy. Le projet prévoit notamment la précision (Precision), le rappel (Recall), le F1-score et l'aire sous la courbe précision-rappel (PR-AUC).

## 3. Description des variables

Le jeu de données contient 31 colonnes :

| Variable | Description |
|---|---|
| `Time` | Nombre de secondes écoulées depuis la première transaction enregistrée dans le jeu de données. Ce n'est pas une date ou une heure civile. |
| `V1` à `V28` | Variables numériques anonymisées obtenues par transformation en composantes principales (PCA). Les variables originales ne sont pas fournies et ces composantes ne peuvent pas être interprétées directement comme des caractéristiques bancaires métier. |
| `Amount` | Montant de la transaction. |
| `Class` | Variable cible : `0` désigne une transaction normale et `1` une transaction frauduleuse. |

Les colonnes `V1` à `V28` sont déjà transformées. Il ne faut donc pas leur attribuer une signification métier non documentée.

## 4. Contrôles de qualité réalisés

Les contrôles initiaux effectués dans le notebook ont donné les résultats suivants :

- **Valeurs manquantes :** aucune valeur manquante détectée.
- **Valeurs infinies :** aucune valeur infinie détectée.
- **Doublons exacts :** 1 081 occurrences supplémentaires, appartenant à 773 groupes distincts.
- **Doublons associés à la classe normale :** 760 groupes.
- **Doublons associés à la classe fraude :** 13 groupes, représentant 32 lignes dans ces groupes.

Les doublons sont étudiés avant toute décision de suppression. La règle de traitement retenue, son motif et les effectifs avant/après seront documentés dans le notebook afin de préserver la traçabilité de la préparation.

## 5. Statistiques descriptives initiales

Quelques statistiques calculées sur le fichier original :

| Variable | Moyenne | Écart-type | Minimum | Médiane (50 %) | Maximum |
|---|---:|---:|---:|---:|---:|
| `Time` | 94 813,8596 | 47 488,1460 | 0 | 84 692 | 172 792 |
| `Amount` | 88,3496 | 250,1201 | 0 | 22 | 25 691,16 |
| `Class` | 0,001727 | 0,041527 | 0 | 0 | 1 |

Les statistiques complètes de toutes les variables (`df.describe()`) et les premières observations (`df.head()`) doivent être conservées dans le notebook exécuté. Elles seront ajoutées à cette documentation à partir de la sortie réelle du notebook, afin d'éviter de retranscrire ou de reconstruire des valeurs.

## 6. Téléchargement et organisation des fichiers

Télécharger manuellement le fichier depuis la page Kaggle indiquée dans la section 1, puis le charger dans Google Colab.

Le fichier brut `creditcard.csv` n'est pas versionné dans ce dépôt. Il est volumineux et reste soumis aux conditions de sa licence. Chaque membre du groupe doit obtenir le fichier depuis la source officielle.

Organisation prévue :

```text
groupe-03-IADS/
├── DATA.md
├── notebooks/
│   └── Credit_Card_Fraud_Detection_Group03.ipynb
├── paper/
└── results/
```

## 7. Préparation des données et prévention des fuites

Les opérations de préparation seront réalisées et justifiées dans le notebook. Le protocole final précisera notamment :

1. la règle retenue pour les doublons exacts ;
2. la séparation des données en ensembles d'entraînement, de validation et de test, avec justification et graine aléatoire ;
3. l'utilisation de la stratification si elle est retenue pour préserver la proportion de fraudes ;
4. l'ajustement des transformations et méthodes de rééquilibrage uniquement à partir des données d'entraînement ;
5. la conservation du jeu de test à l'écart de l'entraînement et du réglage des hyperparamètres.

Aucun résultat de test ne doit être utilisé pour choisir un modèle ou modifier ses paramètres.

## 8. Limites du jeu de données

- Les transactions couvrent seulement deux jours de septembre 2013 : elles ne représentent pas nécessairement les comportements actuels.
- Les variables `V1` à `V28` sont anonymisées et issues d'une transformation PCA ; leur interprétation métier est limitée.
- La classe fraude est très minoritaire, ce qui rend l'évaluation sensible au choix des métriques et du protocole de validation.
- Les résultats obtenus sur ce jeu de données de référence ne garantissent pas les mêmes performances sur des transactions réelles récentes.

## 9. Références

- Machine Learning Group — ULB, *Credit Card Fraud Detection*, jeu de données diffusé sur Kaggle : https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
- Open Data Commons, *Open Database License (ODbL)* : https://opendatacommons.org/licenses/odbl/1-0/

