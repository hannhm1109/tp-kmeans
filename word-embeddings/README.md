# Skip-gram, ACP et K-means sur Word Embeddings

## Description

Ce projet implémente un pipeline complet de traitement de word embeddings en trois étapes:
1. Entraînement d'un modèle Skip-gram (PyTorch)
2. Réduction de dimensionnalité avec ACP (PCA)
3. Clustering K-means avec similarité cosinus

## Objectifs du Projet

- Adapter un modèle CBOW en Skip-gram pour générer des word embeddings
- Visualiser les embeddings dans un espace 2D grâce à l'ACP
- Identifier des groupes sémantiques de mots via K-means
- Utiliser la similarité cosinus (mesure adaptée) au lieu de la distance euclidienne

## Structure du Projet

```
word-embeddings/
├── 1_skipgram_model.ipynb       # Étape 1: Entraînement Skip-gram
├── 2_acp_visualization.ipynb    # Étape 2: Visualisation PCA
├── 3_kmeans_clustering.ipynb    # Étape 3: Clustering K-means
├── CBOW_Model_Pytorch.ipynb     # Code CBOW de référence
├── README.md                     # Ce fichier
└── data/                         # Données générées (optionnel)
    ├── skipgram_model.pth
    ├── embedding_matrix.npy
    ├── embeddings_2d.npy
    ├── cluster_labels.npy
    └── *.pkl
```

## Méthodologie

### Étape 1: Modèle Skip-gram

**Différence CBOW vs Skip-gram:**
- CBOW: Contexte → Mot cible
- Skip-gram: Mot cible → Contexte

**Implémentation:**
- Architecture PyTorch avec embedding layer
- Fenêtre de contexte configurable (window_size=2)
- Optimisation avec SGD et NLLLoss
- Sauvegarde de la matrice d'embeddings (dimension 50)

**Corpus utilisé:**
- Phrases en français sur le Maroc, l'IA et la programmation
- Peut être étendu avec un corpus plus large

### Étape 2: ACP (Analyse en Composantes Principales)

**Objectif:** Réduire de 50 dimensions à 2 pour visualisation

**Processus:**
- Application de PCA avec scikit-learn
- Analyse de la variance expliquée
- Visualisation des mots dans l'espace 2D
- Identification visuelle de groupes sémantiques

**Résultats attendus:**
- Mots similaires proches dans l'espace réduit
- Variance expliquée > 20% (selon le corpus)

### Étape 3: K-means Clustering

**IMPORTANT - Similarité Cosinus:**

Pour les word embeddings, la distance euclidienne n'est PAS appropriée. On utilise la similarité cosinus.

**Solution:** Normalisation L2 des vecteurs avant K-means
- Après normalisation: distance euclidienne ≈ similarité cosinus
- K-means optimise indirectement la similarité cosinus

**Processus:**
1. Normaliser les embeddings (norme L2 = 1)
2. Méthode du coude pour choisir K
3. Score de Silhouette pour validation
4. Application de K-means
5. Interprétation des clusters

**Métriques d'évaluation:**
- Score de Silhouette
- Score de Calinski-Harabasz
- Cohésion intra-cluster (similarité cosinus moyenne)

## Technologies Utilisées

- Python 3
- PyTorch - Deep Learning framework
- NumPy - Calculs numériques
- Scikit-learn - PCA, K-means, métriques
- Matplotlib & Seaborn - Visualisations

## Installation

```bash
pip install torch numpy scikit-learn matplotlib seaborn
```

Pour Colab:
```python
# Tout est déjà installé
import torch
import numpy as np
from sklearn.decomposition import PCA
from sklearn.cluster import KMeans
```

## Utilisation

### Exécution séquentielle:

```bash
# 1. Entraîner Skip-gram
jupyter notebook 1_skipgram_model.ipynb

# 2. Visualiser avec PCA
jupyter notebook 2_acp_visualization.ipynb

# 3. Clustering K-means
jupyter notebook 3_kmeans_clustering.ipynb
```

### Sur Google Colab:

1. Upload les notebooks sur Colab
2. Exécuter dans l'ordre (1 → 2 → 3)
3. Les fichiers .npy et .pkl seront sauvegardés automatiquement

## Résultats Attendus

### Clusters Identifiés

Le nombre de clusters dépend du corpus, mais typiquement:

**Exemple avec corpus Maroc/IA:**
- Cluster 0: Géographie (maroc, rabat, afrique, nord)
- Cluster 1: Intelligence Artificielle (intelligence, artificielle, machine, learning)
- Cluster 2: Programmation (python, programmation, réseaux, neurones)
- Cluster 3: Mots de liaison (est, un, une, le, la, de)

### Visualisations

1. **Évolution de la Loss:** Convergence du modèle Skip-gram
2. **PCA 2D:** Mots proches sémantiquement sont proches visuellement
3. **Clusters colorés:** Groupes distincts dans l'espace PCA
4. **Méthode du coude:** Choix optimal de K

## Points Clés

### Pourquoi la Similarité Cosinus?

**Distance Euclidienne:**
- Mesure la différence absolue entre vecteurs
- Sensible à la magnitude
- Ne capture pas bien la similarité sémantique

**Similarité Cosinus:**
- Mesure l'angle entre vecteurs
- Invariante à la magnitude
- Capture la direction (sémantique)
- Standard en NLP

**Formule:**
```
cosine_sim(A, B) = (A · B) / (||A|| × ||B||)
```

### Normalisation L2

Après normalisation, tous les vecteurs ont une norme de 1:
- Distance euclidienne et similarité cosinus deviennent équivalentes
- K-means peut fonctionner correctement

## Améliorations Possibles

1. **Corpus plus large:** Utiliser un dataset plus conséquent
2. **Embeddings pré-entraînés:** Word2Vec, GloVe, FastText
3. **Clustering hiérarchique:** Alternative à K-means
4. **t-SNE:** Meilleure visualisation que PCA
5. **Évaluation manuelle:** Validation des clusters par des experts

## Compétences Développées

- Implémentation de modèles NLP en PyTorch
- Traitement et analyse de word embeddings
- Réduction de dimensionnalité (PCA)
- Clustering non supervisé
- Choix de métriques adaptées (cosine vs euclidean)
- Visualisation de données haute dimension
- Interprétation de résultats en NLP

## Auteur

Hanane

## Références

- Mikolov et al. (2013) - Efficient Estimation of Word Representations
- Word2Vec Tutorial - https://arxiv.org/abs/1301.3781
- Scikit-learn Documentation - K-means with cosine similarity

---

**Mots-clés:** Skip-gram, Word Embeddings, PCA, K-means, NLP, PyTorch, Cosine Similarity, Clustering, Word2Vec
