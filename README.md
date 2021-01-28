#  :notebook_with_decorative_cover: Valoriser le traitement automatique des données : 

## Le cas des *Ouvriers des deux mondes*
 
:mortar_board: Mémoire pour le [Master TNAH de l'École nationale des chartes](http://www.chartes.psl.eu/fr/cursus/master-technologies-numeriques-appliquees-histoire)

:black_nib: Jean-Damien Généro

:star: dirigé par @alix-tz et @architexte

:calendar: sept. 2020 (🦠)

### Résumé
*Le programme ANR Time Us s’intéresse aux ouvriers et aux ouvrières du textile de la fin du XVIIIe siècle au début du XXe siècle et rassemble pour cela une large documentation composée de documents manuscrits et d'imprimés. Au sein de ces derniers se trouvent les monographies de familles des* Ouvriers des deux mondes *publiées de 1857 à 1930 par Frédéric Le Play (1806-1882) et la Société internationale des études pratiques d’économie sociale.*

*Ce corpus de treize volumes, composé de 114 monographies, a été transcrit et structuré automatiquement au format XML-TEI par un programme utilisant les logiciels d’OCR Transkribus et Kraken, et le langage de programmation Python. Le présent mémoire se propose d'analyser les actions menées au cours d'un stage de fin d'études pour valoriser les résultats de cette structuration automatique, incluant son contrôle, la correction des erreurs et l’usage des humanités numériques pour implémenter un encodage scientifique permettant l’exploitation des données et des transcriptions par les chercheurs et les chercheuses.*

### Mots-clefs

XML ; TEI ; Python ; traitement automatique des données ; transcription automatique ; édition numérique ; ALTO ; OCR ; Kraken ; Transkribus ; GitLab ; Frédéric Le Play ; *Les Ouvriers des deux mondes* ; enquêtes sociologiques ; monographies de familles ; *Time Us* ; Inria.

### Sommaire

I. Un corpus déjà structuré

*A. Un corpus d'imprimé. —  B. Des numérisations multiples. — C. Un encodage automatique.*

II. Une structuration à reprendre

*A. Outils, méthodologie et gestion de projet. — B. Contrôle du découpage des fichiers source. —  C. Découpage éditorial et sémantique.*

III. Des données à valoriser.

*A. Données graphiques, données chiffrées. — B. Données textuelles, données scientifiques. — C. Une valorisation plurielle.*

### Arborescence

```
Memoire-TNAH/
  |
  |── back/
  |     |── annexes
  |
  |── front/
  |     |── page de titre, abréviations, introduction, bibliographie
  |
  |── img/
  |     |── images
  |
  |── main/
  |     |── parties 1-3, conclusion
  |
  |── Memoire_TNAH_OD2M.pdf
  |
  |── enc.bbx & enc.cbx
  |
  |── main.tex (fichier principal avec les packages, les commandes et les includes)
  |
  |── mybibliography.bib (fichier bibliographique)
  |
  |── plan_detaille.md
```

### Citation

Jean-Damien Généro, *Valoriser le traitement automatique des données : Le cas des Ouvriers des deux mondes*, mémoire du Master «&nbsp;Technologies numériques appliquées à l’histoire&nbsp;», dir. A. Chagué et V. Jolivet, École nationale des chartes, 2020.
