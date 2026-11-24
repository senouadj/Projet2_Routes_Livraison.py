# Projet 2 — Optimisation quantique de routes de livraison au Bénin

**Qiskit Fall Fest 2026 • IndabaX Benin • Sèmè City**

**Auteur :** ADJOGAN Senou Gbenoukpo

---

## 1. Présentation du projet

Ce projet a été réalisé dans le cadre du **Qiskit Fall Fest 2026**, organisé au Bénin par IndabaX Benin et iSHEERO, avec le soutien d’IBM Quantum.

L’objectif est de résoudre un problème concret de logistique : **trouver le trajet le plus court** pour un livreur qui doit visiter plusieurs points (marchés ou villes) et revenir à son point de départ, en minimisant la distance totale parcourue.

---

## 2. Objectif

Optimiser la tournée d’un véhicule qui part de **Sèmè City** et doit livrer à :
- Dantokpa
- Porto-Novo
- Ouidah

puis revenir au dépôt, en choisissant l’ordre de passage qui minimise la distance totale.

---

## 3. Formulation du problème

Le problème est une version simplifiée du **Travelling Salesman Problem (TSP)**.

### Variables de décision
Pour chaque paire de points (i, j), on crée une variable binaire :
- `x_i_j` = 1 si le livreur va directement de i vers j
- `x_i_j` = 0 sinon

### Fonction objectif (à minimiser)
Somme des distances de tous les arcs utilisés.

### Contraintes
- Chaque point a **exactement un** arc sortant
- Chaque point a **exactement un** arc entrant

Cela garantit un circuit unique qui visite chaque lieu une seule fois.

---

## 4. Données utilisées

Points considérés :
- 0 : Dépôt (Sèmè City)
- 1 : Dantokpa
- 2 : Porto-Novo
- 3 : Ouidah

Matrice de distances approximatives (en km) :

|            | Depot | Dantokpa | Porto-Novo | Ouidah |
|------------|-------|----------|------------|--------|
| Depot      | 0     | 8        | 30         | 40     |
| Dantokpa   | 8     | 0        | 35         | 45     |
| Porto-Novo | 30    | 35       | 0          | 55     |
| Ouidah     | 40    | 45       | 55         | 0      |

---

## 5. Méthode utilisée

- Modélisation avec `QuadraticProgram` (Qiskit Optimization)
- Résolution avec `MinimumEigenOptimizer` + `NumPyMinimumEigensolver`
- Reconstruction du trajet à partir des variables sélectionnées

---

## 6. Technologies utilisées

- Python 3
- Qiskit
- Qiskit Optimization
- Qiskit Algorithms
- NumPy

---

## 7. Résultats

Le programme affiche :
- La liste ordonnée des trajets (exemple : Depot → Dantokpa → ...)
- La distance de chaque segment
- La **distance totale** du circuit optimal

---

## 8. Comment exécuter le projet

### Installation des dépendances
```bash
pip install qiskit qiskit-aer qiskit-algorithms qiskit-optimization numpy
Lancement
Bashpython Projet2_Routes_Livraison.py

9. Structure du code

Importation des bibliothèques
Définition des points et de la matrice de distances
Création des variables binaires x_i_j
Définition de la fonction objectif (minimisation de la distance)
Ajout des contraintes de degré (un départ et une arrivée par ville)
Résolution du problème
Reconstruction et affichage du trajet optimal


10. Améliorations possibles

Ajouter la capacité du véhicule
Gérer plusieurs véhicules (VRP)
Utiliser de vraies distances (Google Maps / OpenStreetMap)
Prendre en compte les fenêtres horaires de livraison
Visualiser le trajet sur une carte
Tester sur un processeur quantique réel IBM


11. Contexte de réalisation
Ce projet a été préparé en amont du Qiskit Fall Fest 2026 qui se tient le 28 novembre 2026 à Sèmè City (Bénin).
Il montre comment l’optimisation quantique/classique peut être appliquée à des problèmes de logistique réelle au Bénin.

12. Auteur
ADJOGAN Senou Gbenoukpo

Participant sélectionné au Qiskit Fall Fest 2026 – IndabaX Benin

13. Licence
Projet réalisé dans un cadre éducatif et de démonstration.

Libre d’utilisation pour l’apprentissage et la présentation.
