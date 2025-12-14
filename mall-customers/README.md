# Projet Final - ACP et K-means sur Mall Customers

## Description

Ce projet combine l'Analyse en Composantes Principales (ACP) et le clustering K-means pour segmenter les clients d'un centre commercial.

## Dataset - Mall Customers

**200 clients** avec les variables:
- CustomerID
- Genre (Male/Female)
- Age
- Annual Income (k$)
- Spending Score (1-100)

## Methodologie

### 1. Pretraitement
- Normalisation avec MinMaxScaler
- Selection des variables numeriques

### 2. ACP (Analyse en Composantes Principales)
- Reduction a 2 composantes
- Variance expliquee: environ 82% (47.61% + 34.44%)

### 3. K-means Clustering
- 5 clusters identifies
- Comparaison: initialisation aleatoire vs K-means++
- Evaluation avec score Calinski-Harabasz

## Technologies

- Python 3
- Pandas, NumPy
- Scikit-learn (PCA, KMeans, MinMaxScaler)
- Matplotlib, Seaborn

## Installation
```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

## Utilisation
```bash
jupyter notebook Atelier_Acp.ipynb
```

## Resultats

- 5 segments de clients distincts
- Visualisation dans l'espace PCA reduit
- Applications marketing pour ciblage personnalise

## Structure
```
mall-customers/
├── Atelier_Acp.ipynb
├── Mall_Customers.xlsx
└── README.md
```

## Auteur

Hanane

---

**Mots-cles:** PCA, K-means, Customer Segmentation, Clustering, Machine Learning
