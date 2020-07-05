# Plan de mémoire TNAH

Jean-Damien Généro, 6 juillet 2020.

## Valoriser le traitement automatique des données : le cas des *Ouvriers des deux mondes*

### Introduction : le projet Time Us

- Objectifs + contexte ;

- Contexte institutionnel : regroupe plusieurs institutions (conséquences sur le stage : partage de la responsabilité adminsitrative et de l'encadrement entre l'Université de Paris et INRIA) ;

- Étude de plusieurs corpus, dont les *Ouvriers des deux mondes*.

- Les *Ouvriers des deux mondes* : des enquêtes sociologiques initiées par Frédéric Le Play et la Société internationale des études pratiques d'économie sociale.

### I. Un corpus déjà structuré

- Un corpus d'imprimés

  - Une publication sur 60 ans (1857-1928).
  
  - Une structure qui se maintient par-delà les années ?

- Des numérisations multiples.

  - Gallica (texte + images) ;
  
  - Internet Archives (formats multiples) ;
  
  - Caractère incomplet de ces numérisations au regard du corpus global.

- Encodage automatique à partir de la numérisation d'Internet Archive. 

  - Préparation des images.

  - Fonctionnement du script LSE-OD2M : segmentation, transcription, structuration.
  
  - Sortie : 13 fichiers XML source, séparés en 222 fichiers XML, structurés en XML-TEI.
  
### II. Une structuration à reprendre : des tâches manuelles et semi-automatiques

- Méthodologie de travail : 

  - GitLab INRIA ;
  
  - Sharedocs ;
  
  - Feuille de route (issues) (description des missions fixées).

- Niveau corpus : contrôle qualité du découpage des fichiers sources

  - Interventions manuelles pour réparer les erreurs (vérification des fichiers) ;
  
  - Débouché de l'opération : constitution d'un fichier de mapping avec les id des fichiers + implémentation automatique des ces id dans des `@xml:id`.

- Niveau fichier : réparation des erreurs d'implémentation de la structure logique (`<div>` et `<head>`).

  -
