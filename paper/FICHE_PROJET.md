# Fiche projet — Groupe 03

## 1. Titre provisoire

Détection des fraudes par carte bancaire : comparaison de modèles supervisés et non supervisés.

## 2. Question de recherche

Dans quelle mesure la régression logistique, Random Forest et Isolation Forest permettent-ils de détecter efficacement les transactions frauduleuses dans un jeu de données fortement déséquilibré ?

## 3. Hypothèse

Nous faisons l'hypothèse que les performances des modèles diffèrent notamment en matière de détection des fraudes (Recall) et de précision des alertes (Precision), et que l'analyse conjointe de ces métriques permettra d'identifier les compromis les plus pertinents.

## 4. Jeu de données

- **Nom :** Credit Card Fraud Detection
- **Source :** Kaggle
- **Lien :** https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
- **Fichier :** `creditcard.csv`
- **Taille :** 284 807 transactions, dont 492 fraudes (informations descriptives du jeu de données).
- **Licence :** à vérifier sur la page Kaggle avant toute redistribution ou publication.

## 5. Modèles étudiés

1. Régression logistique (Logistic Regression)
2. Random Forest
3. Isolation Forest

## 6. Métriques d'évaluation

- Precision
- Recall
- F1-score
- PR-AUC (aire sous la courbe précision-rappel)

Ces métriques sont retenues pour tenir compte du fort déséquilibre entre les transactions normales et frauduleuses.

## 7. Contribution attendue

Le projet vise à fournir une comparaison expérimentale cohérente de trois approches de détection de fraude, en mettant l'accent sur leur capacité à identifier les transactions frauduleuses dans un contexte de classes fortement déséquilibrées.

## 8. Risques et plan B

- **Déséquilibre des classes :** comparer les métriques adaptées et, si nécessaire, tester une stratégie de pondération des classes ou de rééchantillonnage sur les seules données d'entraînement.
- **Temps de calcul :** limiter les recherches d'hyperparamètres et utiliser un sous-échantillon pour les essais préliminaires.
- **Difficulté de comparaison entre modèles :** expliciter les protocoles et seuils de décision utilisés ; distinguer les modèles supervisés des méthodes de détection d'anomalies.
- **Problème d'accès ou de licence des données :** consulter les conditions de Kaggle et, si le jeu devient indisponible, demander validation de l'enseignant avant de choisir un jeu de données de remplacement.

## 9. Membres et rôles

- **Fanny Mawussé :** rôle à préciser avec l'équipe.
- **Freddy Kaseya :** rôle à préciser avec l'équipe.
- **Rydwane Ichola :** rôle à préciser avec l'équipe.
