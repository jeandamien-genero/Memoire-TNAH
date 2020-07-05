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
  
  - Une structure qui se maintient par-delà les années ? Continuité et discontinuité dans la structure logique des monographies.

- Des numérisations multiples.

  - Gallica (texte + images) et Internet Archives (formats multiples) ;
  
  - Caractère incomplet de ces numérisations au regard du corpus global (monographie manquante).

- Encodage automatique à partir de la numérisation d'Internet Archive. 

  - Préparation des images.

  - Fonctionnement du script LSE-OD2M : segmentation, transcription, structuration.
  
  - Sortie : 13 fichiers XML source, séparés en 222 fichiers XML, structurés en XML-TEI.
  
### II. Une structuration à reprendre : des tâches manuelles et semi-automatiques

- Méthodologie de travail : 

  - GitLab INRIA et Sharedocs ;
  
  - Feuille de route (issues : description des missions fixées).

- Niveau du corpus : contrôle qualité du découpage des fichiers source.

  - Interventions manuelles pour corriger les erreurs (vérification des fichiers) ;
  
  - Débouché de l'opération : constitution d'un fichier de mapping avec les id des fichiers + implémentation automatique des ces id dans des `@xml:id`.

- Niveau du fichier : correction des erreurs d'implémentation de la structure logique (`<div>` et `<head>`).

  - Typologie des erreurs et causes probables (distance d'édition trop faible entre certains mots des titres ? + problème de détection des figures de type image ou tableau) ;
  
  - Impossibilité d'automatiser complètement la correction des erreurs (script Python avec des regex pour reconstruire les `<div>` + script pour contrôler la structure logique = pas efficace à 100% en raison d'un nombre de cas particuliers très élevés ) ;
  
  - Cette opération a mis en évidence un autre problème : la transcription d'en-tête, de bas de page, de numéros de page ou de numéros de cahier autour avant ou après les `<pb>`, qu'il faut là encore supprimer afin de garantir une bonne reconstitution des paragraphes dans l'hypothèse d'une publication.
  
  - Script de validation des fichiers au regard des guidelines TEI, lancé sur le cluster RIOC d'INRIA.
  
### III. Un corpus à valoriser : quelle place pour l'automatisation ?

- Quelles images conserver ? 

  - Choix de ne garder que le lien vers les images d'Internet Archive et de supprimer celles stockées localement.
  
  - Script de substitution automatique (https://timeus.hypotheses.org/645).

- Indexer les individus :

  - Constitution automatique d'un fichier XML d'index à partir d'un tableau prosopographique.
  
  - Impossibilité d'implémenter les balises d'indexation (`<persName>`) dans les fichiers du fait de la qualité des transcriptions.
  
- Corriger les transcriptions ?

  - Dans le cadre d'une exploitation de données, peu d'intérêt d'avoir une transcription parfaite. Or possibilité au minimum de mettre à disposition des fichiers XML au mieux sur de publier les textes (par ex. sur Wikisource). Comment parvenir un état qui permet deux exploitation différentes (niveau données, niveau texte) ?
  
  - Projet Time Us : intérêt pour les les §2 et §8 des monographies. Corrections pourraient se concentrer sur ces paragraphes.
  
  - Comment ? Librairies Grammalecte ou pyspellchecker ?
  
- (Si je peux le faire avant la fin du stage) Implémentation d'une DTS pour permettre une citation de passage précis.

### Conclusion : perspectives d'améliorations.

- (Si je n'ai pas le temps) DTS ;
  
- Index des figures ;
  
- Intégrer l'histoire matérielle des fascicule au sein du `<teiHeader>`;
  
- Base de données prosopographique à partir de l'index ;
  
- Relever les renvois entre monographie et leur donner une réalité au sein de la TEI.
  
- Édition en ligne ?
