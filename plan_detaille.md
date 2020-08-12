# Valoriser le traitement automatique des données : le cas des *Ouvriers des deux mondes*

Plan détaillé du mémoire TNAH de Jean-Damien Généro, 17 juillet 2020.

Réflexion : quelles sont les implications de la production d'un corpus semi-automatisée pour la recherche ?

---

### Introduction : le projet Time Us

- Objectifs + contexte ;

- Contexte institutionnel : regroupe plusieurs institutions (conséquences sur le stage : partage de la responsabilité administrative et de l'encadrement entre l'Université de Paris et INRIA) ;

- Étude de plusieurs corpus, dont les *Ouvriers des deux mondes*.

- Les *Ouvriers des deux mondes* : des enquêtes sociologiques initiées par Frédéric Le Play et la Société internationale des études pratiques d'économie sociale, numérisées sur Internet Archive et structurées en XML-TEI par le projet TIME US.

- Mon intervention : 

  - Objectif côté pro : reprendre les fichiers XML et les valoriser de manière semi-automatique.
  
  - Objectif côté recherche : quelle est la valeur ajoutée de l'automatisation pour l'exploitation d'une documentation dans le cadre d'un projet de recherche ? 
  
---

### I. Un corpus déjà structuré

#### A. Un corpus d'imprimés

  - Une publication sur 60 ans (1857-1928).
  
  - Une structure qui se maintient par-delà les années ? Continuité et discontinuité dans la structure logique des monographies.

#### B. Des numérisations multiples

  - Gallica (texte + images) et Internet Archives (formats multiples) ;
  
  - Caractère incomplet de ces numérisations au regard du corpus global (monographies manquantes).

#### C. Encodage automatique à partir de la numérisation d'Internet Archive

  - Préparation des images.

  - Fonctionnement du script LSE-OD2M : segmentation, transcription, structuration ([billet d'Alix](https://timeus.hypotheses.org/626)).
  
  - Sortie : 13 fichiers XML source, séparés en 222 fichiers XML, structurés en XML-TEI  (avec reprise d'éléments issus de LaTeX pour caractériser les divisions : *chapter*, *section*, *subsection*, *subsubsection*, etc).
  
  - Point d'entrée du stage : corpus structuré dans lequel plusieurs points ont été identifiés comme devant être re-travaillés. Corpus composé des enquêtes sociologiques (les monographies) et d'éléments de paratexte. Chercheurs intéressés uniquement par les premières, volonté de traiter l'ensemble lors du stage.

---
  
### II. Une structuration à reprendre : des tâches manuelles et semi-automatiques

#### A. Gestion de projet : méthodologie de travail

  - Mise en place d'outils de développement : GitLab INRIA (versionnage par commits, feuille de route dans les issues, merge requests, Pylint pour l'intégration continue) ;
  
  - Mise en place d'espaces de discussion : GitLab INRIA (issues et merge requests), MatterMost, Zoom (conséquence du télé-travail) ;
  
  - Typologie des points/erreurs à reprendre.

#### B. Niveau du corpus : contrôle qualité du découpage des fichiers source.

*À lire : [Best Practices for TEI in Libraries](https://tei-c.org/extra/teiinlibraries/4.0.0/bptl-driver.html).*

  - Vérification de la cohérence documentaire par rapport à l'unité codicologique d'origine : la structure a-t-elle été bien retranscrite ? Quels sont les cas particuliers ? 

  - Interventions manuelles pour corriger les erreurs (vérification des fichiers) ;
  
  - Débouché de l'opération : constitution d'un fichier de mapping avec les id des fichiers + implémentation automatique des ces id dans des `@xml:id` + fichier `master.xml` avec des `<xi:include>`.

#### C. Niveau du fichier : correction des erreurs d'implémentation de la structure logique (`<div>` et `<head>`).

  - Typologie des erreurs et causes probables (distance d'édition trop faible entre certains mots des titres ? + problème de détection des figures de type image ou tableau) ;
  
  - Impossibilité d'automatiser complètement la correction des erreurs (script Python avec des regex pour reconstruire les `<div>` + script pour contrôler la structure logique = pas efficace à 100% en raison d'un nombre de cas particuliers très élevés ) ;
  
  - Cette opération a mis en évidence un autre problème : la transcription d'en-tête, de bas de page, de numéros de page ou de numéros de cahier autour avant ou après les `<pb>`, qu'il faut là encore supprimer afin de garantir une bonne reconstitution des paragraphes dans l'hypothèse d'une publication.
  
  - Script de validation des fichiers au regard des guidelines TEI, lancé sur le cluster RIOC d'INRIA, procédé SSH, connexion à un serveur distant, gain de temps.
  
---

### III. Un corpus à valoriser : quelle place pour l'automatisation ?

- Valorisation de la donnée se fait sur deux niveaux :

  - Donnée brute (standardisation, pérennisation, documentation) : nécessite un schéma (ODD = définir en amont la pratique éditoriale et s'y conformer) et un historique des interventions (Git) ;
  
  - Donnée mise en scène (publication, mise à disposition du public de chercheur) : plateforme de publication.

#### A. Lier le texte aux images des pages ? 

  - Choix de ne garder que le lien vers les images d'Internet Archive et de supprimer celles stockées localement.
  
  - Script de substitution automatique (https://timeus.hypotheses.org/645).
  
  - Pour une publication future : *quid* du IIIF ? (L'image est affichée dans le contexte de l'application depuis le serveur d'Internet Archive ou Gallica avec ses métadonnées et la possibilité de feuilleter le volume.)

#### B. Indexer les individus ?

  - Travail en amont d'un chercheur : constitution manuelle d'un tableau prosopographique des individus enquêtés. Possibilité de le faire de manière automatique ? Problème posé par la reconnaissance d'entités nommées "personne", très difficile car la transcription et mauvaise et qu'il faudrait un corpus plus important.

  - Constitution automatique d'un fichier XML d'index à partir de ce tableau.
  
  - Impossibilité d'implémenter les balises d'indexation (`<persName>`) dans les fichiers du fait de la qualité des transcriptions. Solution d'attente, implémentation d'un commentaire avec le individus et leurs id, mais cela constitue une dette technique pour plus tard.
  
#### C. Corriger les transcriptions ?

  - Dans le cadre d'une exploitation de données, peu d'intérêt d'avoir une transcription parfaite. Or possibilité au minimum de mettre à disposition des fichiers XML au mieux de publier les textes (par ex. sur Wikisource). Comment parvenir un état qui permet deux exploitations différentes (niveau données, niveau texte) ?
  
  - Projet Time Us : intérêt pour les les §2 et §8 des monographies. Corrections pourraient se concentrer sur ces paragraphes.
  
  - Nécessité d'analyser la qualité textuelle du corpus.
  
  - Comment ? Librairies Grammalecte ou pyspellchecker ?

---

### Conclusion : perspectives d'amélioration.

  - Quelles tâches ont pu être automatisées ? Quelles tâches ont résisté à l'automatisation ?
  
  - Les scripts sont-ils réutilisables ?
  
  - Dans quel état est le corpus à la fin du stage ?
  
  - Que reste-il à faire ? Qu'est-ce qui peut être envisagé pour la suite ?

    - DTS (quelle granularité de citation ?) ;
  
    - Index des figures ;
  
    - Intégrer l'histoire matérielle des fascicule au sein du `<teiHeader>`;
  
    - Base de données prosopographique à partir de l'index ;
  
    - Relever les renvois entre monographie et leur donner une réalité au sein de la TEI.
  
    - Édition en ligne, mise à disposition des textes ?
