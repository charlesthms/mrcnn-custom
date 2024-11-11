# Rapport d'entraînement du Modèle

---


## Vue d'ensemble
Ce rapport détaille le processus d'entraînement et les résultats de notre modèle, incluant les logs, des exemples du jeu de données, les graphes de perte, la matrice de confusion, les hyperparamètres, et les observations finales.

## 1. Logs

```
Epoch 1/5
100/100 [==============================] - 1575s 16s/step - loss: 3.4451 - val_loss: 2.5046
Epoch 2/5
100/100 [==============================] - 1553s 16s/step - loss: 2.3474 - val_loss: 2.3218
Epoch 3/5
100/100 [==============================] - 1554s 16s/step - loss: 1.8803 - val_loss: 1.3393
Epoch 4/5
100/100 [==============================] - 1527s 15s/step - loss: 1.7480 - val_loss: 0.9975
Epoch 5/5
100/100 [==============================] - 1522s 15s/step - loss: 1.6851 - val_loss: 1.1672
```
_Dernière Ligne du Journal :_  
Perte d’Entraînement (dernier epoch) : **1.6851**  
Perte de Validation (dernier epoch) : **1.1672**

## 2. Exemples du Jeu de Données
Voici quelques exemples tirés du jeu de données, incluant des échantillons utilisés pour l'entraînement, la validation et le test.

![Exemple d'Entraînement 1](https://raw.githubusercontent.com/Souhila06/Souhila06.github.io/refs/heads/main/images/maksssksksss0.png)
![Exemple d'Entraînement 2](https://raw.githubusercontent.com/Souhila06/Souhila06.github.io/refs/heads/main/images/maksssksksss1.png)

## 3. Matrice de Confusion
La matrice de confusion ci-dessous montre les performances du modèle sur le jeu de données de test.

![Matrice de Confusion](path/to/confusion_matrix.png)

## 4. Graphe des Pertes

Les graphs ci-dessous montrent la progression des pertes d'entraînements et de validations au cours de chaque epoch, lors de nos apprentissages nous avons utilisé ce graph afin d'étudier la convergence du modèle pour détecter le sur-apprentissage et adapter le nombre d'epochs nécessaire.

![Pertes d'Entraînement et de Validation](path/to/loss_graph.png)

## 5. Hyperparamètres
Le tableau suivant résume les hyperparamètres que nous avons testés lors de l'entraînement et la valeur finale que nous avons utilisé.

| Hyperparamètre       | Valeur(s) Testée(s)        | Valeur Finale        |
|----------------------|----------------------------|-----------------------|
| Taux d'Apprentissage (lr) | `0.001`, `0.005`, `0.01` | `0.001`           |
| Optimiseur           | `SGD`, `Adam`   | `Adam`               |
| Epochs               |  `100`, `250`, `500`  |  `100`                |
| Régularisation       | `L1: 0.001`, `L1: 0.0001`  | `Pas de L1, uniquement le régularisateur L2 par défaut` |

## 6. Observations et Commentaires
Basé sur les résultats, voici quelques observations et réflexions générées manuellement :

- **Convergence du Modèle :** Les pertes d'entraînement et de validation montrent [décrire tout surapprentissage, sous-apprentissage ou comportements de convergence observés]. Cela suggère que [insérer une explication concernant le comportement d'entraînement, comme un entraînement suffisant ou le besoin de plus de données/de l'augmentation de données].
  
- **Efficacité des Hyperparamètres :** Parmi les hyperparamètres testés, [mentionner quels paramètres ont positivement impacté les performances, le cas échéant]. Par exemple, le taux d'apprentissage de `0.001` avec l'optimiseur `Adam` a permis une bonne convergence.

- **Analyse de la Matrice de Confusion :** Le modèle a bien performé sur [mentionner les classes bien prédites] mais a eu des difficultés avec [mentionner les classes ou instances problématiques]. Cela pourrait être dû à [raisons potentielles des erreurs comme un déséquilibre des classes, des données insuffisantes pour certaines classes, etc.].

- **Améliorations Suggérées :** Les itérations futures du modèle pourraient bénéficier de [suggérer des améliorations supplémentaires, telles que plus de données, ajustement des hyperparamètres, ou des techniques avancées].

---

> _Ce rapport fournit une vue complète des performances du modèle, démontrant à la fois ses forces et les domaines à améliorer._

---
