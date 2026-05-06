# Calcul de Malliavin & Pricing d'Option Asiatique : Étude Numérique

Ce dépôt présente une étude numérique sur l'évaluation et l'estimation des Grecques (Delta) d'une option asiatique complexe sous le modèle de Bachelier. Ce travail a été réalisé dans le cadre du cours de Malliavin Calculus du Master 2 MMMEF (Modélisation et Méthodes Mathématiques en Économie et Finance) de l'Université Paris 1 Panthéon-Sorbonne.

## 📌 Présentation du Projet

L'objectif principal de cette étude est de comparer l'efficacité de deux méthodes numériques pour l'estimation du Delta d'une option :
1.  **La méthode des Différences Finies (FD)** : Une approche classique par "bumping" de la trajectoire.
2.  **Le Calcul de Malliavin (Intégration par parties - IBP)** : Une méthode probabiliste avancée permettant de calculer les sensibilités sans avoir à dériver la fonction de payoff.

## 🧮 Cadre Mathématique & Paramètres

Le sous-jacent est modélisé selon un **Modèle de Bachelier** avec les paramètres suivants :
*   Condition initiale ($x_0$) : 100.0
*   Taux sans risque ($r$) : 10%
*   Maturité ($T$) : 1.0 an
*   Strike du Call : 100.0
*   Barrière : 110.0

Le payoff étudié est celui d'un call vanille conditionné par une barrière sur l'intégrale de la trajectoire de l'actif (caractéristique asiatique).
Les simulations de Monte Carlo sont évaluées sur différentes grilles de temps ($M \in [10, 20, 50, 100, 150, 250]$) et pour des tailles d'échantillon ($N$) allant jusqu'à 50 000 trajectoires.

## 📊 Principaux Résultats & Analyse de Convergence

L'implémentation de ces méthodes et l'étude de la variance empirique ont permis de tirer les conclusions suivantes :

*   **Validation de la convergence** : Les deux méthodes (FD et IBP) convergent avec succès vers une valeur de Delta cohérente (environ 0.45 pour $M=50$).
*   **Stabilité des Différences Finies** : L'estimateur FD se révèle extrêmement robuste. Sa variance empirique reste très faible et constante (environ 0.19).
*   **Instabilité de la méthode de Malliavin (IBP)** : L'approche IBP présente une variance énorme, environ 10 fois supérieure à celle de la méthode FD (oscillants entre 2.3 et 2.6). La convergence est donc très bruitée, même avec un grand nombre de trajectoires ($N=50000$).

**Bilan** : Pour ce profil de payoff spécifique, la méthode standard des Différences Finies est nettement plus performante. L'approche par le Calcul de Malliavin nécessiterait l'implémentation de techniques de réduction de variance pour devenir numériquement compétitive.

## 👨‍💻 Auteur

Fevzi BOZCA
Master 2 MMMEF - Université Paris 1 Panthéon-Sorbonne
