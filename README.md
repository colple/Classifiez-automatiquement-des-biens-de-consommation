# CLASSIFIEZ AUTOMATIQUEMENT DES BIENS DE CONSOMMATION

## Cinquième projet de ma formation de Data Scientist

## Contexte

<p align="center">
  <img src="logo_place_de_marche.png" alt="Texte alternatif">
</p>

Vous êtes Data Scientist au sein de l’entreprise "Place de marché”, qui souhaite lancer une marketplace e-commerce.

Sur la place de marché, des vendeurs proposent des articles à des acheteurs en postant une photo et une description.

Pour l'instant, l'attribution de la catégorie d'un article est effectuée manuellement par les vendeurs, et est donc peu fiable. De plus, le volume des articles est pour l’instant très petit.

Pour rendre l’expérience utilisateur des vendeurs (faciliter la mise en ligne de nouveaux articles) et des acheteurs (faciliter la recherche de produits) la plus fluide possible, et dans l'optique d'un passage à l'échelle, il devient nécessaire d'automatiser cette tâche.

## Préambule
Ce projet a été réalisé en langage Python dans des notebooks Jupyter, ainsi qu'un notebook Google Collab.

## Les données

Les données sont disponibles à l'adresse suivante: https://s3-eu-west-1.amazonaws.com/static.oc-static.com/prod/courses/files/Parcours_data_scientist/Projet+-+Textimage+DAS+V2/Dataset+projet+pre%CC%81traitement+textes+images.zip 

## Missions
Linda, Lead Data Scientist, vous demande donc d'étudier la faisabilité d'un moteur de classification des articles en différentes catégories, avec un niveau de précision suffisant.

**Mission 1: Etude de faisabilité d'un moteur de classification d'articles, basé sur une image et une description, pour l'automatisation de l'attribution de la catégorie de l'article**
1. Analyse des descriptions textuelles et les images des produits, au travers des étapes suivantes:
    - Prétraitement des données texte ou image
    - Extraction de features
    - Réduction en 2 dimensions, afin de projeter les produits sur un graphique 2D, sous la forme de points dont la couleur correspondra à la catégorie réelle
    - Analyse du graphique afin d’en déduire ou pas, à l’aide des descriptions ou des images, la faisabilité de regrouper automatiquement des produits de même catégorie
    - Réalisation d’une mesure pour confirmer ton analyse visuelle, en calculant la similarité entre les catégories réelles et les catégories issues d’une segmentation en clusters
2. Contraintes pour l'extraction des features texte
    - Mise en oeuvre de deux approches de type “bag-of-words”: comptage simple de mots et Tf-idf
    - Mise en oeuvre d'une approche de type word/sentence embedding classique avec Word2Vec (ou Glove ou FastText)
    - Mise en oeuvre d'une approche de type word/sentence embedding avec BERT
    - Mise en oeuvre d'une approche de type word/sentence embedding avec USE (Universal Sentence Encoder)
3. Contraintes pour l'extraction des features des images
    - Mise en oeuvre d'un algorithme de type SIFT / ORB / SURF
    - Mise en oeuvre d'un algorithme de type CNN Transfer Learning
      
**Mission 2: Réalisation d'une classification supervisée à partir des images *via* la mise en place d'une data augmentation afin d’optimiser le modèle**

**Mission 3: Test de la collecte de produits à base de “champagne” à partir d'une API (https://rapidapi.com/edamam/api/edamam-food-and-grocery-database)**
1. Souhait d'élargir la gamme de produits, en particulier dans l’épicerie fine.
2. Extraction des 10 premiers produits dans un fichier “.csv”, contenant pour chaque produit les données suivantes : foodId, label, category, foodContentsLabel, image.

## Contenu de ce dépôt
1. Le notebook Jupyter pour l'étude de faisabilité d'un moteur de classification d'articles basé sur le texte: notebook_1_faisabilite_texte.ipynb.
2. Un notebook réalisé sur Google Collab pour l'étude de faisabilité d'un moteur de classification d'articles basé sur le texte *via* USE: notebook_1bis_special_use.ipynb.
3. Le notebook Jupyter pour l'étude de faisabilité d'un moteur de classification d'articles basé sur les images: notebook_2_faisabilite_images.ipynb.
4. Le notebook Jupyter pour la classification supervisée d'images *via* l'algorithme d'optimisation rmsprop: notebook_3_classification_supervisee_rmsprop.ipynb.
5. Le notebook Jupyter pour la classification supervisée d'images *via* l'algorithme d'optimisation adam: notebook_3bis_classification_supervisee_adam.ipynb.
6. Le notebook Jupyter contenant le script pour l'extraction des 10 premiers produits à base de champagne: notebook_4_script_requete_api.ipynb.
7. La présentation des résultats du projet sous format pdf: presentation_5.pdf.
8. L'extraction des 10 premiers produits à base de champagne sous format csv: extraction_api_6.csv.
9. La liste des librairies nécessaires à la réalisation du projet: requirements.txt.
10. Le logo de Place de marché: logo_place_de_marche.png

## Compétences acquises
1. Prétraitement des données textes pour l'obtention d'un jeu de données exploitable:
    - Nettoyage des champs de texte (suppression de la ponctuation *via* le RegexpTokenizer et des mots de liaison, mise en minuscules)
    - "Lemmatisation " des phrases (voire "lemmatisation").
    - Etapes supplémentaires de nettoyage: Conservation des mots anglais d'au moins 3 lettres, élimination des tokens uniques, élimination des éléments des adresses URL et HTML, élimination des caractères non-ascii et conservation unique des noms et des verbes.
2. "Feature extraction" des données textuelles par plusieurs approches:
    - Approche de type bag of words (sac de mots): comptage de mots et Tf-idf.
    - Notion de l'approche de type word/sentence embedding (plongement de mots): Word2Vec, BERT et USE (Universal Sentence Encoder).
3. Prétraitement des données images pour l'obtention d'un jeu de données exploitable: Utilisation de Pillow pour le retraitement des images (contraste, filtrage du bruit de fond et floutage)
4. "Feature extraction" des données images par plusieurs approches:
    - Notion de bag of images *via* la génération de descripteurs (algorithme SIFT): Non performant.
    - Notion d'extraction des features *via* un algorythme de Transfer Learning (CNN) basé sur des réseaux de neurones.
5. Réduction dimensionnelle: PCA suivie d'un T-SNE:
    - LA PCA permet:(i) le maintien d'une variance expliquée élevée à 99%, (ii) la création de features décorrélées entre elles et (iii) la réduction de la dimensionnalité afin de réduire le temps de traitement du T-SNE.
    - Le T-SNE permet la réduction en 2 composantes pour la visualisation en 2D des catégories de produits.
6. Notion de la stratégie d’élaboration d’un modèle d'apprentissage profond utilisant des modèles pré-entraînés (transfer learning) et entraînement des modèles afin de réaliser une analyse prédictive.
7. Évaluation de la performance des modèles d’apprentissage profond selon différents critères (scores, temps d'entraînement, etc.) afin de choisir le modèle le plus performant pour la problématique métier.
8. Utilisation des techniques d’augmentation des données afin d'améliorer la performance des modèles.
9. Définition de la stratégie de collecte de données *via* une API.

## Auteur
**Coline Plé**
