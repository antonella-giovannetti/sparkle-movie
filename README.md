# 🎥 Système de Recommandation de Films - Projet MovieLens

## 📌 Contexte du projet

Dans le cadre de l'amélioration de l'expérience utilisateur sur une **plateforme de streaming vidéo**, nous avons développé un **système de recommandation personnalisé** de films. Ce type de système est utilisé quotidiennement par des entreprises comme Netflix, Amazon Prime, ou Disney+ pour suggérer aux utilisateurs des contenus susceptibles de leur plaire.

Pour ce projet, nous utilisons l'ensemble de données **MovieLens 100k**, une base de données populaire pour tester les algorithmes de recommandation.



## 📊 Objectif principal

Créer un **moteur de recommandation de films** capable de proposer à chaque utilisateur une liste de films qu’il pourrait aimer, en se basant sur :
- Son historique d’évaluations de films.
- Les comportements d'autres utilisateurs similaires.



## 📁 Structure du projet

Le projet est contenu dans un notebook Jupyter : `eda.ipynb`.  
Il suit les étapes suivantes :

1. **Chargement des données**
2. **Prétraitement et nettoyage**
3. **Analyse exploratoire (EDA)**
4. **Construction du modèle de recommandation**
5. **Évaluation des performances**
6. **Génération de recommandations personnalisées**



## 📦 Données utilisées : MovieLens 100k

- **Nombre d’utilisateurs** : 943  
- **Nombre de films** : 1 682  
- **Nombre d’évaluations** : 100 000  
- **Format des données** :
  - `userId` : identifiant utilisateur
  - `movieId` : identifiant du film
  - `rating` : note entre 1 et 5
  - `timestamp` : date de l’évaluation


## 🧪 Librairies utilisées

Voici les principales bibliothèques utilisées dans le projet :

- `pyspark` : manipulation des données
- `numpy` : opérations numériques
- `matplotlib` / `seaborn` : visualisation
- `scikit-learn` : machine learning
- `surprise` : librairie spécialisée pour les systèmes de recommandation
- `jupyter notebook` : environnement d'exécution



## 🔍 Étapes détaillées

### 1. Chargement et exploration initiale

On commence par importer les données et explorer leur structure :
- Vérification des valeurs manquantes
- Aperçu des utilisateurs et des films
- Statistiques globales sur les notes (moyenne, médiane…)

### 2. Nettoyage et préparation

- Transformation des colonnes (e.g. timestamp → date)
- Encodage des identifiants
- Fusion avec d’autres fichiers si besoin (ex: titres de films)
- Filtrage des utilisateurs/films avec peu d’activité

### 3. Analyse exploratoire (EDA)

Objectif : **mieux comprendre les comportements utilisateurs**.
Quelques analyses réalisées :
- Distribution des notes
- Films les mieux/mal notés
- Films les plus évalués
- Activité des utilisateurs (nombre de notes par utilisateur)

Visualisations :
- Histogrammes
- Graphiques en barres
- Matrices de corrélation

### 4. Création du modèle de recommandation

Nous utilisons la librairie **Surprise** pour implémenter plusieurs modèles de recommandation :

#### 📍 Approches testées :
- **Filtrage collaboratif user-user** : recommande des films qu’ont aimé les utilisateurs semblables.
- **Filtrage item-item** : recommande des films similaires à ceux aimés par l’utilisateur.
- **SVD (Singular Value Decomposition)** : technique de factorisation matricielle qui permet de représenter utilisateurs et films dans un même espace latent.

#### 🔧 Implémentation :
- Chargement des données dans un format adapté (`Dataset.load_from_df`)
- Entraînement des modèles via `train_test_split`
- Évaluation avec RMSE (Root Mean Squared Error)
- Recommandation de top-N films par utilisateur

### 5. Évaluation du modèle

- Séparation des données en **jeu d’entraînement** et **jeu de test**
- Calcul du **RMSE** sur les prédictions
- Comparaison entre différents modèles pour sélectionner le meilleur

### 6. Génération de recommandations

Une fois le modèle entraîné :
- Pour chaque utilisateur, on prédit les notes des films non vus.
- On trie ces prédictions par ordre décroissant.
- On recommande les N films avec les meilleures prédictions.

Exemple :

The Matrix (4.95)

The Godfather (4.90)

Pulp Fiction (4.89)

Forrest Gump (4.88)

The Shawshank Redemption (4.85)




## 📈 Résultats obtenus

Le modèle **SVD** a obtenu les meilleurs résultats avec un **RMSE < 0.9**, ce qui signifie que les prédictions sont assez proches des notes réelles données par les utilisateurs.

Le système est capable de générer des recommandations pertinentes et personnalisées.


## ✅ À venir

Fonctionnalités futures possibles :
- Ajouter un moteur de recherche de films
- Créer une interface web avec Streamlit ou Flask
- Intégrer un système de feedback pour améliorer les suggestions
- Utiliser un modèle hybride (collaboratif + contenu)

---


