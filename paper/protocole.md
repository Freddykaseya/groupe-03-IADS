# Protocole expérimental — Détection de fraude par carte bancaire

## 1. Objectif

L’objectif est de comparer plusieurs approches de détection des transactions frauduleuses à partir du jeu de données **Credit Card Fraud Detection** (ULB / Kaggle). La variable cible est `Class` : 0 pour une transaction normale et 1 pour une transaction frauduleuse.

Le jeu de données est fortement déséquilibré : les transactions frauduleuses représentent environ **0,173 %** des observations. Une évaluation fondée uniquement sur l’accuracy serait donc insuffisante.

## 2. Modèles retenus dès la conception du projet

La sélection initiale comprend un modèle de référence et trois approches complémentaires. Ces modèles ont été retenus pour comparer des stratégies différentes sur un problème de classification tabulaire très déséquilibré.

| Modèle | Type | Rôle dans l’expérience | Justification du choix |
|---|---|---|---|
| Dummy Classifier | Baseline | Établir un niveau de référence minimal | Fournit un point de comparaison simple. Il permet de vérifier si les modèles entraînés apportent réellement une amélioration par rapport à une stratégie naïve. |
| Logistic Regression | Supervisé | Première approche de classification | Modèle de référence simple et interprétable pour une classification binaire. Il permet d’établir une première performance avant d’utiliser des modèles plus complexes. |
| Random Forest | Supervisé | Approche non linéaire par ensemble d’arbres | Permet de modéliser des relations non linéaires et des interactions entre variables, sans supposer une relation linéaire entre les caractéristiques et la cible. |
| Isolation Forest | Non supervisé — détection d’anomalies | Approche complémentaire sans apprentissage direct sur les étiquettes | Permet d’examiner la détection des transactions atypiques comme des anomalies. Cette approche apporte un point de comparaison différent des classificateurs supervisés. |

**Important :** cette sélection correspond aux modèles prévus dès le début du projet. Elle constitue un choix expérimental à évaluer, et non une affirmation selon laquelle ces modèles seraient nécessairement les meilleurs.

## 3. Principes de comparaison

Les modèles seront évalués sur des données séparées de celles utilisées pour leur entraînement. Le protocole de séparation des données, le traitement du déséquilibre, les hyperparamètres et les seuils de décision devront être documentés dans le notebook avant l’évaluation finale.

Les résultats seront comparés à l’aide des métriques suivantes :

- **Precision** : proportion des transactions signalées comme frauduleuses qui sont réellement frauduleuses.
- **Recall** : proportion des fraudes réelles détectées par le modèle.
- **F1-score** : moyenne harmonique de la précision et du rappel.
- **PR-AUC** : aire sous la courbe précision-rappel, particulièrement pertinente lorsque la classe positive est très minoritaire.

L’accuracy pourra être rapportée à titre complémentaire, mais ne sera pas utilisée seule pour conclure sur la qualité d’un modèle.

## 4. Points de vigilance

- Toute opération de prétraitement ou de rééquilibrage doit être ajustée uniquement sur les données d’entraînement afin d’éviter les fuites de données.
- Le jeu de test doit rester indépendant et être utilisé pour l’évaluation finale.
- Le seuil de décision doit être explicité. Pour Isolation Forest, les scores d’anomalie et la règle de conversion en prédictions binaires doivent être documentés séparément.
- Les performances doivent être interprétées en tenant compte du coût des faux positifs et des faux négatifs.

## 5. Éléments à compléter après les expériences

Les éléments suivants seront renseignés une fois le protocole d’entraînement fixé et les expériences exécutées :

- stratégie exacte de séparation train / validation / test ;
- méthode éventuelle de gestion du déséquilibre ;
- hyperparamètres retenus et méthode de sélection ;
- seuils de décision utilisés ;
- résultats comparatifs et analyse des erreurs.
