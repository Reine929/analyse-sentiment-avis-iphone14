# Analyse de sentiment d'avis clients : iPhone 14

Projet réalisé individuellement, pendant un cours de mon Bachelor Business Intelligence & Data à Nexa Digital School.

## Objectif

À partir d'un jeu de données d'avis sur des téléphones, étudier les avis sur l'iPhone 14 et comparer deux modèles d'analyse de sentiment, VADER et TextBlob, avec les avis déjà étiquetés (positif, neutre, négatif) comme référence.

## Ce que fait le notebook

1. **Préparation** avec Pandas : lecture du fichier CSV, sélection des colonnes utiles, filtre sur le modèle iPhone 14 (1 788 avis : 1 015 positifs, 423 neutres, 350 négatifs), nettoyage du texte (minuscules, suppression des liens et des caractères spéciaux).
2. **Analyse de la variable cible** : diagramme de répartition des sentiments et nuages de mots des avis positifs et négatifs.
3. **Modèle VADER** (NLTK) : score « compound », classement en négatif, neutre ou positif avec un seuil de neutralité, rapport de classification, matrice de confusion (Seaborn) et interprétation.
4. **Modèle TextBlob** : même démarche avec le score de polarité.
5. **Comparaison** des deux modèles et conclusion.

## Résultats

| Modèle | Seuil de neutralité | Exactitude (accuracy) |
| --- | --- | --- |
| VADER | ±0,5 | 59 % |
| TextBlob | ±0,1 | 77 % |

## Limites

- Les seuils de neutralité (±0,5 pour VADER, ±0,1 pour TextBlob) n'ont pas été optimisés et ne sont pas identiques : la comparaison des deux modèles est donc à nuancer. Un seuil plus étroit pour VADER pourrait changer son résultat.
- Les avis neutres sont mal classés par les deux modèles (VADER en retrouve 50 % mais se trompe souvent, TextBlob en retrouve 37 %).
- Les textes d'avis se répètent beaucoup : environ 110 formulations différentes pour les 1 788 avis. Les scores mesurent donc surtout la capacité des modèles sur un petit nombre de phrases types.
- L'analyse porte sur un seul modèle de téléphone et sur des avis en anglais.

## Lancer le projet

1. Installer les dépendances : `pip install -r requirements.txt`
2. Placer dans le même dossier le fichier CSV d'avis, nommé `Mobile Reviews Sentiment(in).csv` (non inclus dans ce dépôt).
3. Ouvrir `analyse_sentiment_avis_iphone14.ipynb` avec Jupyter et exécuter les cellules dans l'ordre. Le lexique de VADER est téléchargé automatiquement par NLTK. Le notebook est fourni avec ses résultats ; les chiffres ci-dessus correspondent à son exécution sur le fichier d'avis utilisé.

## Outils

Python, Pandas, NLTK (VADER), TextBlob, scikit-learn, Seaborn, Matplotlib, WordCloud, Jupyter.
