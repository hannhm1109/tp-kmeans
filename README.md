# TP K-Means - Clustering avec données aléatoires

## Description
Ce TP implémente l'algorithme de clustering **K-means from scratch** et l'applique sur des données aléatoires générées synthétiquement.

## Contenu

### Exercices couverts:
- **Génération de données synthétiques** avec `make_blobs`
- **Implémentation from scratch** de l'algorithme K-means
- **Visualisation** des clusters et centroïdes  
- **Calcul et affichage** de l'inertie intra et inter-classes

### Structure du code:
1. Génération de 100 points aléatoires en 2D avec 4 centres
2. Classe `Kmeans` custom avec:
   - Initialisation aléatoire des centroïdes
   - Calcul de distances euclidiennes
   - Attribution aux clusters
   - Mise à jour des centroïdes
3. Fonctions d'évaluation: inertie intra-classes et inter-classes
4. Visualisation avec matplotlib et seaborn

## Technologies utilisées
- Python 3
- NumPy
- Matplotlib
- Seaborn  
- Scikit-learn (pour génération de données)

## Résultats
Le notebook montre:
- Les clusters formés par l'algorithme
- L'évolution des inerties au fil des itérations
- Comparaison visuelle entre les vrais labels et les clusters trouvés

## Auteur
Hanane
