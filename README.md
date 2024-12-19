
# Systèmes de Recommandation

Ce dépôt contient deux implémentations de systèmes de recommandation :  
1. **Système de Recommandation Basé sur le Contenu**  
2. **Système de Recommandation Basé sur les Évaluations des Utilisateurs**

Ces systèmes visent à fournir des recommandations personnalisées pour les films, en utilisant différentes approches de filtrage et de calcul de similarité.

---

## Table des matières

1. [Prérequis](#prérequis)  
2. [Installation](#installation)  
3. [Utilisation](#utilisation)  
4. [Description des fichiers](#description-des-fichiers)  
5. [Fonctionnalités](#fonctionnalités)  
6. [Méthodes principales](#méthodes-principales)  

---

## Prérequis

Assurez-vous d'avoir installé les bibliothèques Python suivantes :  

- **Pandas** : pour la manipulation des données.  
- **NumPy** : pour les calculs mathématiques.  
- **scikit-learn** : pour la vectorisation et le prétraitement.  
- **gc** : pour la gestion de la mémoire (pour le système basé sur les évaluations des utilisateurs).

Installez les bibliothèques avec :

```bash
pip install pandas numpy scikit-learn
```

---

## Installation

Clonez le dépôt et accédez au répertoire correspondant :  

```bash
git clone https://github.com/anasnedday/RecommendationSystems.git
cd RecommendationSystems
```

---

## Utilisation

### 1. **Système de Recommandation Basé sur le Contenu**

- Préparez vos fichiers CSV :  
  - **movies.csv** : Contient au moins `movieId`, `title`, `genres`.  
  - **ratings.csv** : Contient au moins `userId`, `movieId`, `rating`.

- Configurez les chemins des fichiers dans la classe `ContentBasedRecommender`.

- Exécutez le script pour obtenir des recommandations :

```python
recommender = ContentBasedRecommender("movies.csv", "ratings.csv")
user_id = 1
recommended_movies = recommender.recommend_movies(user_id, n_recommendations=10)
print(f"Films recommandés pour l'utilisateur {user_id} : {recommended_movies}")
```

### 2. **Système de Recommandation Basé sur les Évaluations des Utilisateurs**

- Préparez vos fichiers CSV :  
  - **movies.csv** : Contient au moins `movieId` et `title`.  
  - **ratings.csv** : Contient au moins `userId`, `movieId`, `rating`.

- Configurez les chemins des fichiers dans la classe `System_Recommender`.

- Exécutez le script pour obtenir des recommandations :

```python
recommender = System_Recommender("movies.csv", "ratings.csv")
user_id = 1
recommended_movies = recommender.make_user_recommendations(user_id, n_recommendations=10)
print(f"Films recommandés pour l'utilisateur {user_id} : {recommended_movies}")
```

---

## Description des fichiers

1. **movies.csv** :  
   - `movieId` : Identifiant unique du film.  
   - `title` : Titre du film.  
   - `genres` : Liste des genres associés au film, séparés par `|` (pour le système basé sur le contenu).

2. **ratings.csv** :  
   - `userId` : Identifiant unique de l'utilisateur.  
   - `movieId` : Identifiant du film noté.  
   - `rating` : Note donnée par l'utilisateur au film (entre 1 et 5).  

---

## Fonctionnalités

### **1. Système Basé sur le Contenu**

1. **Prétraitement des Données** : Remplissage des genres manquants et vectorisation des genres avec `CountVectorizer`.  
2. **Calcul de Similarité Cosinus Manuelle** : Calcule la similarité entre les films en utilisant une implémentation sans dépendances externes.  
3. **Recommandations Personnalisées** : Recommande des films non vus, basés sur la similarité avec les films déjà appréciés.  

### **2. Système Basé sur les Évaluations des Utilisateurs**

1. **Filtrage Collaboratif Utilisateur-Utilisateur** :  
   - Basé sur la corrélation de Pearson entre les utilisateurs.  
2. **Prétraitement des Données** :  
   - Applique un seuil minimal d'évaluations pour les utilisateurs et les films.  
3. **Recommandations Personnalisées** :  
   - Propose des films à un utilisateur donné en fonction des goûts similaires d'autres utilisateurs.  

---

## Méthodes principales

### **1. Système Basé sur le Contenu**

1. **`_prep_data()`** : Prépare les données et transforme les genres en vecteurs numériques.  
2. **`_compute_similarity_matrix()`** : Calcule la similarité cosinus manuelle entre les films.  
3. **`recommend_movies(user_id, n_recommendations)`** : Génère des recommandations personnalisées pour un utilisateur donné.  

### **2. Système Basé sur les Évaluations des Utilisateurs**

1. **`_prep_data()`** : Prépare les données des films et des utilisateurs.  
2. **`_pearson_similarity(user1, user2)`** : Calcule la similarité de Pearson entre deux utilisateurs.  
3. **`_inference(user_id)`** : Identifie les films à recommander en fonction des utilisateurs similaires.  
4. **`make_user_recommendations(user_id, n_recommendations)`** : Génère les recommandations finales de films pour un utilisateur spécifique.  

