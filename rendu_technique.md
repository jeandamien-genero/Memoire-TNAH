# Mémoire TNAH : rendu technique
Jean-Damien Généro, *Valoriser le traitement automatique des données : Le cas des Ouvriers des deux mondes*, mémoire du Master « Technologies numériques appliquées à l’histoire », dir. Alix Chagué et Vincent Jolivet, École nationale des chartes, 2020.

## Arborescence du dossier

```
Mémoire/
	|
	|- 0_corpus-od2m-fixture#7/
	|		|
	|		|- copie de la branche fixture#7 = dépôt GitLab au début du stage (avril 2020).
	|
	|- 1_corpus-od2m-master/
	|		|
	|		|- copie de la branche master = dépôt GitLab à la fin du stage (sept. 2020).
	|
	|- repository_GitLab/
	|		|
	|		|- corpus-od2m = clone du dépôt Gitlab avec les branches master et fixture#7.
	|
	|- Les_Ouvriers_des_deux_mondes_Toronto/
	|		|
	|		|- volumes au format PDF téléchargés d'Internet archive
	|
	|- GENERO_Memoire_TNAH_OD2M.pdf/
```

## Contenu du repository Git

Les dossiers 0_corpus-od2m-fixture#7, 1_corpus-od2m-master et repository_GitLab/corpus-od2m ont le même contenu présenté selon différents états d'avancement.

Le repository Git est organisé de la façon suivante :

```
corpus-od2m
	|
	|- source/
	|	|- fichiers XML des 13 volumes des Ouvriers des deux mondes
	|
	|- files/
	|	|
	|	|- (fixture#7) 223 fichiers XML correspondant aux chapitres
	|	|
	|	|- (master) 194 fichiers XML correspondant aux chapitres
	|				master_od2m.xml : fichier avec les includes
	|				index_od2m.xml : index des enquêtés au format XML
	|				ODD_OD2M.xml : schéma ODD
	|					|
	|					|- out/ schéma RNG
	|
	|- script/ scripts python
	|
	|- metadata/
		|
		|- cartographies du corpus (mapping_....csv)
		|
		|- od2m_id_internet_archives.csv : identifiants des volumes sur Internet archive
		|
		|- od2m_table_struct_logique.pdf : tableau synoptique des titres des chapitres
		|
		|- images_per_monographie[.json,.csv]
		|
		|- images_per_chapter.json
		|
		|- Json_OD2M_Internet_Archives/
		|		|
		|		|- json contenant les metadonnées des images, dont leurs adresses (issue 2)
		|		
		|- Internet_Archives_IIIF/
				|- manifestes IIIF des volumes
```

## Liste des scripts Python

* `add_iiif.py` et `replace_img_filesnames_by_url.py` : permettent de compléter l'attribut @url de `<graphic>` par l'adresse IIIF ou JPEG de l'image (issue 2) ;

* `basic_iteration.py` : permet d'itérer sur l'ensemble des fichiers pour faire des rechercher/remplacer basiques (toutes les issues).

* `change_atype_in_graphic_to_figure.py` : permet de changer de niveau l'attribut @type qui passe de `<graphic>` à `<figure>` (révision de la structure logique).

* `change_xml_id.py` : permet d'insérer les IDs des fichiers dans le @xml:id de `<TEI>` et le @ana de `<div>` (révision de la structure logique).

* `delete_tags_and_attrs.py` : supprime les balises `<zone>` et les attributs @facs des `<p>` et `<head>` (révision de la structure logique).

* `make_index_comments.py` : à partir d'un fichier CSV d'index, écrit un commentaire dans le paragraphe 2 des monographies avec la liste des individus enquêtés et leurs identifiants (issue 4).

* `make_index.py` : crée un fichier d'index XML à partir d'un CSV (issue 4).

* `make_list_of_images_per_chapter.py` : script d'Alix Chagué.

* `replace_img_filesnames_by_url.py` : cf. `add_iiif.py`.

* `rng_validator.py` : contrôle la validité d'un corpus de fichiers XML par rapport à un schéma RNG.

* `split_volumes_in_chapter.py` : script d'Alix Chagué.

* `write_includes.py` : écrit des xi:includes dans un fichier master.xml.
