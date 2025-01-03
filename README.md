# Rapport d'entrainement d'un modèle - IA M2 

## Groupe
- YOUSFI Souhila
- THOMAS Charles

---

Mise à jour et cohérence des données (28/12/24)

- La matrice de confusion fournie n'est pas basée sur les images mais
 sur le nombre de masques détecté sur chaque image ce qui explique les 1600 résultats.

- L'optimizer final est effectivement Adam car notre version avec SGD n'a pas été concluante.

- Le graph des loss montre un entrainement sur 10 epochs afin de rendre visible l'overfiting
 et de montrer pourquoi nous avons décidé de faire un entrainement limité à 3 epochs

- Source du dataset : https://www.kaggle.com/datasets/andrewmvd/face-mask-detection

## Vue d'ensemble
Ce rapport détaille le processus d'entraînement et les résultats de notre modèle, incluant les logs, des exemples du jeu de données, les graphes de perte, la matrice de confusion, les hyperparamètres, et les observations finales.

Ce répertoire contient les notebook utilisés pour entrainer et évaluer le modèle dans le dossier ```/src/eval.ipynb``` et ```/src/train.ipynb```

## 1. Jeu de Données
Voici quelques exemples tirés du jeu de données. Notre dataset contient 200 images que nous avons annotées avec l'outil **VIA**. Le fichier exporté est nommé annotations.json dans ```/src/annotations.json```

![data](./images/maksssksksss101.png)
![data](./images/maksssksksss102.png)
![data](./images/maksssksksss103.png)




## 2. Hyperparamètres
Le tableau suivant résume les hyperparamètres que nous avons testés lors de l'entraînement et la valeur finale que nous avons utilisé.

| Hyperparamètre       | Valeur(s) Testée(s)        | Valeur Finale        |
|----------------------|----------------------------|-----------------------|
| Learning Rate | `0.001`, `0.005`, `0.01` | `0.001`           |
| Optimizer           | `SGD`, `Adam`   | `Adam`               |
| Steps per Epoch               |  `100`, `250`, `500`  |  `100`                |
| Epochs             |  `3`, `5`, `10`, `20`  |  `3`                |
| Regularization       | `L1: 0.001`, `L1: 0.0001`  | `Pas de L1, uniquement le régularisateur L2 par défaut` |
|IMAGE_MAX_DIM | `512`, `1024` | `512` |

## 3. Logs

![data](./images/logs.png)
*SCREENSHOT des logs de l'entrainement*

_Dernière Ligne du log :_  
Perte d’Entraînement (dernier epoch) : **1.2681**  
Perte de Validation (dernier epoch) : **1.3899**

## 4. Loss Graph

Les graphs ci-dessous montrent la progression des pertes d'entraînements et de validations au cours de chaque epoch, lors de nos apprentissages nous avons utilisé ce graph afin d'étudier la convergence du modèle pour détecter le sur-apprentissage et adapter le nombre d'epochs nécessaire.

![Pertes d'Entraînement et de Validation](./images/epoch_loss_v1.jpg)

On peut remarquer que l'entrainement overfit à partir de 2 epochs (en partant de 0) nous avons donc entrainé le modèle sur **3 epochs** par la suite

## 5. Matrice de Confusion
La matrice de confusion ci-dessous montre les performances du modèle sur le jeu de données de test entrainé sur 3 epochs.

![Matrice de Confusion](./images/confusion_matrix_v1.png)

## 6. Exemples de détections
Voici quelques exemples provenant de différentes versions de notre modèle, on peut voir des erreur dans nos tests qui ont mené à un modèl sous-entrainés et parfois de fausses détections provenants d'un sur-entrainement. Finalement nous avons conservé le modèle le plus équilibré.

D'autres évaluations sont disponibles dans le notebook eval.ipynb

![Exemple2](./images/detection.png)
![Exemple1](./images/fail.png)


## 7. Observations et Commentaires
Basé sur les résultats, voici quelques observations et réflexions générées manuellement :
  
- **Efficacité des Hyperparamètres :** Parmi les hyperparamètres testés, pour notre dataset, le taux d'apprentissage de `0.001` avec l'optimiseur `SGD` a permis la meilleur convergence.

- **Analyse de la Matrice de Confusion :** On peut  conclure que notre modèle est performant mais pourrait être perfectible en testant d'autres paramètres, en faisant attention à ne pas être dans un cas d'overfiting.

---
