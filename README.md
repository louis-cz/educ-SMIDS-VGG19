# educ-SMIDS-VGG19

Projet de classification d'images de spermatozoïdes, dans le cadre de l'UE **MLB** de l'université de Rennes. Le jeu de données utilisé est appelé **SMIDS** (Sperm Morphology Image Data Set) et est disponible [ici](https://link.springer.com/article/10.1007/s11517-019-02101-y). Le code est largement inspiré de [cette exploitation](https://www.kaggle.com/code/orvile/sperm-morphology-classification-pytorch) disponible sur Kaggle.

⚙️ python, pytorch, seaborn, matplotlib, pandas, numpy

## Structure du projet
- `data/` : Dossier contenant les résultats des modèles testés.
- `img/` : Dossier contenant les graphiques issus des analyses des résultats.
- `PJ_MLB.pdf` : Rapport du projet.
- `PJ_MLB.ipynb` : Notebook Jupyter contenant le code du projet.

## Méthodologie & résultats

Choix du modèle en deux temps : à partir d'un modèle pré-entrainé VGG19, plusieurs types d'entrée et d'architectures du réseau ont été testés (tableau 1). Le modèle final a été affiné par une recherche d'hyperparamètres (tableau 2).

**Tableau 1 : Comparaison des architectures testées.**
| Modèle | Canaux | Augmentation de données | Dropout | Précision (%) | Recul (%) |
| ------ | ------ | ----------------------- | ------- | ------------- | --------- |
| A.0    | gris   | Non                     | Non     | /             | /         |
| B.0    | RGB    | Non                     | Non     | /             | /         |
| C.0    | gris   | Oui                     | Non     | /             | /         |
| D.0    | RGB    | Oui                     | Non     | /             | /         |
| E.0    | gris   | Oui                     | Oui     | /             | /         |
| F.0    | RGB    | Oui                     | Oui     | /             | /         |

**Tableau 2 : Résultats de la recherche d'hyperparamètres sur le modèle final (F.0).**
| Modèle | Blocs dégelés | Fonction d'optimisation | Taux d'apprentissage | Précision (%) | Recul (%) |
| ------ | ------------- | ----------------------- | -------------------- | ------------- |
| F.0    | non           | Adam                    | 0.0001               | /             | /         |
| F.1    | oui (1)       | Adam                    | 0.0001               | /             | /         |
| F.2    | non           | SGD                     | 0.0001               | /             | /         |
| F.3    | non           | Adam                    | 0.00001              | /             | /         |
| F.4    | non           | Adam                    | 0.001                | /             | /         |

Le modèle final retenu est le **modèle F.0**, avec une précision de / % et un recul de / % sur le jeu de test.

Pour aller plus loin, des analyses complémentaires ont été réalisées comme une analyse des cartes d'activation. Ces analyses sont disponibles dans le notebook Jupyter `PJ_MLB.ipynb` et illustrées par des graphiques dans le dossier `img/`. Exemple : 
![F.0 - Normal classif](img/normal_act.png)
