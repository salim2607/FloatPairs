# TP 2 : Résolution du Problème FloatPairs avec JMetalPy

## 📋 Description

Ce projet implémente le problème d'optimisation **FloatPairs** en utilisant le framework JMetalPy. L'objectif est de maximiser le comptage des paires de flottants de signes différents dans une séquence de nombres.

## ✅ TODO List - Suivi des Tâches

### Phase 1 : Implémentation du Problème
- [ ] Créer la classe `FloatPairsMax` héritant de `Problem`
- [ ] Implémenter la méthode `__init__`
- [ ] Implémenter la méthode `evaluate` (comptage des paires)
- [ ] Implémenter la méthode `create_solution`
- [ ] Tester le problème avec des exemples simples

### Phase 2 : Recherche Locale
- [ ] Adapter le code pour la recherche locale
- [ ] Configurer `PolynomialMutation`
- [ ] Tester différents paramètres
- [ ] Effectuer 20 runs de la recherche locale
- [ ] Collecter les résultats (moyenne, médiane, écart-type, temps)
- [ ] Créer des graphiques des résultats

### Phase 3 : Algorithme Génétique
- [ ] Adapter le code pour l'algorithme génétique
- [ ] Configurer `PolynomialMutation`
- [ ] Configurer `SBXCrossover`
- [ ] Tester différentes configurations de paramètres
- [ ] Effectuer 20 runs pour chaque configuration
- [ ] Collecter les résultats (moyenne, médiane, écart-type, temps)
- [ ] Créer des graphiques comparatifs

### Phase 4 : Analyse et Comparaison
- [ ] Analyser l'influence des paramètres sur la convergence
- [ ] Définir un protocole de comparaison équitable
- [ ] Comparer Recherche Locale vs Algorithme Génétique
- [ ] Réaliser des tests statistiques (si nécessaire)
- [ ] Créer des visualisations comparatives

### Phase 5 : Rapport
- [ ] Rédiger l'introduction
- [ ] Documenter l'implémentation
- [ ] Présenter les résultats de la recherche locale
- [ ] Présenter les résultats de l'algorithme génétique
- [ ] Rédiger l'analyse comparative
- [ ] Rédiger la conclusion
- [ ] Relire et corriger le rapport
- [ ] Préparer le ZIP final (rapport + codes)

### Bonus (Optionnel)
- [ ] Implémenter d'autres algorithmes (PSO, ES, etc.)
- [ ] Tester sur différentes tailles de problèmes
- [ ] Analyser la scalabilité des algorithmes
- [ ] Créer un dashboard interactif des résultats

## 🎯 Objectif du Problème

Le problème FloatPairs cherche à maximiser le nombre de paires adjacentes de flottants ayant des signes différents dans une séquence.

### Définition d'une Paire

Une paire est constituée de deux nombres flottants **adjacents** de **signes différents** :
- Exemple : (-5.0, 3.0) ou (6.0, -2.5)

### Exemple de Calcul

Pour `n=8`, `borne_inf = -10.00`, `borne_sup = 10.00`

**Solution :** `[-10.00, 5.00, 6.25, 3.14, -8.7, -9.75, 1.36, -9.99]`

**Paires identifiées :**
- Position 1-2 : `-10.00` et `5.00` ✓
- Position 4-5 : `3.14` et `-8.7` ✓
- Position 6-7 : `-9.75` et `1.36` ✓
- Position 7-8 : `1.36` et `-9.99` ✓

**Score total : 4 paires**

## 🔧 Implémentation

### Structure du Problème

Le problème FloatPairs hérite de la classe `Problem` de JMetalPy. Inspiré de l'implémentation de FloatSum, voici la structure de base :

```python
class FloatPairsMax(Problem):
    def __init__(self, number_of_floats, min_value, max_value):
        super().__init__()
        # Configuration des paramètres
        # Définition des objectifs
        # Initialisation des bornes
    
    def evaluate(self, solution):
        # Calcul du nombre de paires adjacentes de signes différents
        pass
```

### Ressources

- [Documentation JMetalPy](https://jmetal.github.io/jMetalPy/tutorials/problem.html)
- Référence : Implémentation de FloatSum fournie dans le TP

## 🧪 Expérimentations

### 1. Recherche Locale

**Tâches :**
- Adapter le code pour une recherche locale sur FloatPairs
- Utiliser `PolynomialMutation` (adapté aux solutions à valeurs réelles)
- Expérimenter différents paramètres
- Effectuer **20 runs**

**Métriques à collecter :**
- Moyenne des scores
- Médiane
- Écart-type
- Temps de calcul par run

### 2. Algorithme Génétique

**Tâches :**
- Implémenter un algorithme génétique pour FloatPairs
- Utiliser :
  - `PolynomialMutation` pour la mutation
  - `SBXCrossover` pour le croisement
- Tester différentes configurations de paramètres
- Effectuer **20 runs** pour chaque configuration

**Métriques à collecter :**
- Moyenne des scores
- Médiane
- Écart-type
- Temps de calcul par run

## 📊 Analyse des Résultats

### Questions à Explorer

1. **Influence des paramètres :** Quelle est l'influence des différents paramètres sur la convergence de l'algorithme ?

2. **Comparaison équitable :** Comment comparer équitablement les algorithmes ?

3. **Comparaison des approches :** Recherche Locale vs Algorithme Génétique

4. **Protocole expérimental :** Proposition et réalisation d'un protocole d'évaluation rigoureux

## 📁 Structure du Projet

```
.
├── src/
│   ├── problems/
│   │   └── float_pairs.py          # Implémentation du problème
│   ├── algorithms/
│   │   ├── local_search.py         # Recherche locale
│   │   └── genetic_algorithm.py    # Algorithme génétique
│   └── utils/
│       └── statistics.py            # Outils d'analyse statistique
├── experiments/
│   ├── local_search_results/
│   └── genetic_algorithm_results/
├── docs/
│   └── rapport.pdf                  # Rapport détaillé
└── README.md
```

## 🚀 Installation

```bash
# Cloner le repository
git clone https://github.com/votre-username/floatpairs-jmetalpy.git

# Installer les dépendances
pip install jmetalpy
pip install numpy pandas matplotlib
```

## 💻 Utilisation

```python
from src.problems.float_pairs import FloatPairsMax
from jmetal.algorithm.singleobjective.local_search import LocalSearch

# Créer le problème
problem = FloatPairsMax(
    number_of_floats=8,
    min_value=-10.0,
    max_value=10.0
)

# Lancer une recherche
algorithm = LocalSearch(problem=problem, ...)
algorithm.run()
result = algorithm.get_result()
```

## 📈 Résultats

Les résultats détaillés des 20 runs pour chaque algorithme sont disponibles dans le dossier `experiments/` et synthétisés dans le rapport.

## 📝 Rendu

**Format :** Fichier ZIP contenant :
- Rapport PDF complet
- Codes Python
- Résultats expérimentaux

**Modalités :** Travail individuel ou binôme

**Date limite :** [À compléter]

## 👥 Auteurs

- [Votre Nom]
- [Nom du binôme] (optionnel)

## 📄 Licence

Ce projet est réalisé dans le cadre d'un TP académique.

---

## 🔗 Références

- [JMetalPy Documentation](https://jmetal.github.io/jMetalPy/)
- [JMetalPy GitHub](https://github.com/jMetal/jMetalPy)

---

## 📝 Notes

Pour cocher une tâche terminée, remplacez `- [ ]` par `- [x]` dans le fichier README.md