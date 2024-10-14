# Système de Recommandation Basé sur les Évaluations des Utilisateurs

Ce projet implémente un système de recommandation collaboratif basé sur la **similarité utilisateur-utilisateur** en utilisant la corrélation de Pearson. Le but est de recommander des films à un utilisateur en fonction des évaluations des autres utilisateurs qui ont des goûts similaires.

## Table des matières

1. Prérequis
2. Installation
3. Utilisation
4. Description des fichiers
5. Fonctionnalités
6. Méthodes principales


## Prérequis

Assurez-vous d'avoir installé les bibliothèques Python suivantes :

- **Pandas** : pour la manipulation des données.
- **NumPy** : pour les calculs mathématiques.
- **gc** : pour la gestion de la mémoire.

```bash
pip install pandas numpy scikit-learn
```

## Installation
```bash
git clone https://github.com/anasnedday/RecommandationBasedUsers.git
cd recommandation-system
``` 
## Utilisation

1. Préparez vos fichiers CSV de films et d'évaluations d'utilisateurs :
-movies.csv : Doit contenir au moins deux colonnes movieId et title.
-ratings.csv : Doit contenir au moins trois colonnes userId, movieId et rating.
2. Mettez à jour les chemins des fichiers dans la classe System_Recommender.
3. Exécutez le fichier principal pour obtenir des recommandations:

## Fonctionnalités

1. Filtrage collaboratif utilisateur-utilisateur : Basé sur la corrélation de Pearson entre les utilisateurs.
2. Prétraitement des données : Seuil minimal d'évaluations pour les utilisateurs et les films afin d'améliorer la qualité des recommandations.
3. Recommandations personnalisées : Propose des recommandations de films à un utilisateur donné en fonction des goûts similaires d'autres utilisateurs.

## Méthodes principales

1. **_prep_data()** : Prépare les données des films et des utilisateurs.
2. **_pearson_similarity()** : Calcule la similarité entre deux utilisateurs.
3. **_inference()** : Génère des recommandations basées sur les utilisateurs similaires.
4. **_make_user_recommendations()** : Génère les recommandations finales de films pour un utilisateur spécifique.