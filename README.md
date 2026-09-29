# Détecteur d'URLs malveillantes

Classification binaire (bénigne / malveillante) d'URLs avec Python, pandas et scikit-learn.

## Données
Dataset Kaggle "Malicious URLs dataset" (651 191 URLs). Les classes phishing, defacement et malware sont regroupées en "malveillante" (1) ; "benign" = 0 (428 103 bénignes, 223 088 malveillantes).

Dataset : [Malicious URLs dataset (Kaggle)](https://www.kaggle.com/datasets/sid321axn/malicious-urls-dataset), environ 651 000 URLs classées en benign, phishing, defacement et malware.

## Méthode
- 8 features extraites de l'URL : longueur, nombre de points, de tirets, de chiffres, de slashs, présence de "@", d'une adresse IP, de mots suspects.
- Séparation 80 % entraînement / 20 % test, arbre de décision (DecisionTreeClassifier).

## Résultats
| Modèle | Accuracy | Faux négatifs | Rappel (classe 1) |
|---|---|---|---|
| 5 features | 0,8135 | 16 197 | 0,64 |
| 8 features | 0,8911 | 7 461 | 0,83 |

## Limites
- nb_slash est la feature la plus importante. Sans elle, l'accuracy tombe à environ 0,82. Elle capte peut-être en partie le préfixe "http://", présent surtout sur les URLs malveillantes du dataset (hypothèse non vérifiée).
- Un seul modèle, sans validation croisée.

## Pistes d'amélioration
Features supplémentaires, comparaison avec Random Forest, validation croisée.
