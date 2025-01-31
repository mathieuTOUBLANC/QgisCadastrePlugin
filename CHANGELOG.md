# CHANGELOG

## Version 1.8.0

**IMPORTANT**
À partir de cette version seule la version QGIS LTR sera supportée. Pour cette version il s'agit de la version 3.4.x

Nouveautés:

* Prise en charge des évolutions MAJIC 2019 (voir #192 pour les détails). Noter la création de 2 nouvelles tables.
* Précisions sur les versions QGIS, PostgreSQL / PostGIS et Spatialite supportées (#197)
* Mise à jour de la documentation de la structure de la base de données (#204)


## Version 1.7.1

* Refactorize code for server and Qgis 3+
* Ajouts et mises à jour de tables domaine
* Correction valeur compte communal
* Ajout inspireid
* Amélioration de plugin Server
* Nouvelle table de nomenclature natvoi
* Correction identifiants
* trim code de nature de voie
* [Serveur] Add GetCapabilities method to server CADASTRE service
* Creation d'un provider QgsProcessing

## Version 1.7.0

* Fiche parcellaire - Ajout des informations des propriétaires, subdivisions et locaux
* Fiche parcelle - Ajout de la surface spatiale bâtie
* Export (version QGIS 2): Ajout d'un script python pour exporter les relevés PDF via ligne de commande
* Fix - Général: Amélioration de la récupération d'informations sur les couches (hôte, base de données, etc.)
* Fix - Import: Suppression de table temporaire ll si besoin
* Fix - Export: relevé de propriété: dédoublonnage des comptes communaux exportés en PDF
* Fix - Correction d'un bug d'encodage
* Divers - Ajout des derniers financeurs dans le dialogue "A propos"

## Version 1.6.2

* Général - suppression de code inutile suite à la migration QGIS3
* Import - Correction de parcelles en doublons dû au lien avec geo_subdsect
* Export PDF - Correction d'un bug et restauration de l'affichage des propriétaires

## Version 1.6.1

* Correction de bug sur l'interrogation de propriétaire suite à la gestion des dates en texte
* Correction d'un bug d'encodage sur message d'erreur de requête SQL
* Import - Utilisation d'entiers longs pour les surfaces de parcelle_info (corrige le bug pour les très grandes parcelles)
* Import - Ajout du support du millésime 2018

## Version 1.6.0

* Compatibilité du plugin avec QGIS 3. Les version compatibles avec QGIS 2 seront des versions de correction uniquement, avec un numéro en 1.5.*

## Version 1.5.2

* Import - Transformation des champs date en texte pour le MAJIC, par respect de la donnée source
* Correction d'un bug de la 1.5.1 avec QFileDialog, QFileInfo et BaseError manquant

## Version 1.5.1

* Import - MAJIC : correction de bug si dates mauvaises (30 fév par ex)
* Import - Support partiel des données EDIGEO en projection IGNF
* Import - Correction d'un bug de non remplissage des parcelles si correspondance geo_subdsect manquant
* Import - EDIGEO : conversion en date des champs de geo_subdsect seulement si format correct #120

## Version 1.5.0

* Chargement - Ajout de couches via requête SQL
* Import - Ajout de la nomenclature pour ccocac
* Import - Correction sur la table pivot geo_batiment_parcelle: restriction par intersection
* Rechercher - Déplacement de la recherche d'adresse sous celle par parcelle
* Chargement - correction d'un bug sur l'ajout dans les groupes Cadastre
* Import - Ajout du support de MAJIC 2017
* Recherche - Support de l'autocomplétion pour les adresses et les propriétaires
* Recherche - Intégration des adresses dans la recherche de lieux
* Import - Correction du bug de récupération des propriétés bâties
* Import/Identification - contournement du bug d'encodage sur requête pour QGIS 2.18.10 et >
* Identification - correction du bug sur chargement de projet QGIS
* Import - Majic : import des propriétaires si et seulement si dnupro est non vide
* Import - Lieudits: utilisation de tous les champs tex
* Recherche - Réapplication de l'ordre dans les listes déroulantes (sections, parcelles)
* BDD - Possibilité de se connecter avec un connexion utilisant un service PostgreSQL

## Version 1.4.1

* Import/Chargement - correction de bug pour Spatialite sur génération parcelle_info

## Version 1.4.0

* Menu - Suppression du menu Cadastre et déplacement dans le menu Extensions
* Barre d'outil - Modification de l'icône d'identification (merci @pasqual )
* Structure bdd - Généralisation des codes départements et direction dans les identifiants
* Structure bdd - Parcelles: consolidation des infos propriétaires dans une nouvelle table parcelle_info
* Import - Correction d'un bug de remplissage de geo_sym si ptcanv_id.sym est NULL
* Import - MAJIC: Filtrage des données importées selon département et direction: on peut utiliser le fichier FANTOIR national
* Import - Ajout du support de MAJIC 2016
* Import - Edigeo : amélioration de la jointure de geo_parcelle ave geo_subdsect
* Import - Correction des doublons sur les parcelles (dus au lien geo_subdsect)
* Import - Edigeo: amélioration des performances pour tpoint, tline, tsurf
* Import - Augmentation de la limite max pour le code direction - fixes #94
* Import - Utilisation directe des fichiers sources sans copie préalable
* Import - Suppression des contraintes de taille dans les champs
* Import - Déplacement des scripts SQL d'import et nettoyage
* Import - Fantoir recommandé lors de l'import MAJIC && lien de téléchargement ajouté
* Import - Correction des parcelles dupliquées si plusieurs sous-sections
* Import - correction du bug empêchant la création de base sqlite sous 2.16 - #83
* Chargement - Ajout du filtre par expression sur les communes (expérimental)
* Chargement - possibilité de charger seulement les couches principales
* Chargement - Séparation des étiquettes et des données en groupes & désactivation des couches mineures
* Chargement - Mise à jour et amélioration des styles
* Chargement - Correction de bug sur QgsMapLayer non défini
* Chargement - Styles : masquage de la couche Tronçons de routes aux petites échelles
* Export - Ajout d'un nouveau menu pour exporter la vue courante en PDF
* Export - ajout d'une carte en 1ère page pour le relevé parcellaire
* Export - Ouverture automatique du répertoire après export PDF multiple
* Recherche - La recherche par commune et section utilise le lot pour éviter les doublons si plusieurs départements
* Serveur - Ajout de la capacité "server" pour le plugin

## Version 1.3.0

* Import - MAJIC : support du millésime 2015. La structure a été un peu modifiée. Il faut réaliser l'import dans un nouveau schéma PostGreSQL ou une nouvelle base de données Spatialite. Un script de migration de la structure est disponible pour PostGreSQL pour ceux qui préfèrent conserver le schéma actuel (faites une sauvegarde avant !) : /.qgis2/python/plugins/cadastre/scripts/plugin/updates/update_structure_postgis_from_1.2.0_to_1.3.0.sql
* Import - Ajout d'un système de création des tables manquantes ( pour les montées de version )
* Edigeo - Ajout des objets TRONROUTE dans la table geo_tronroute
* Import - Éviter l'import des parcelles EDIGEO avec un idu NULL
* Plugin - Suppression de la contrainte de version maximum de QGIS

## Version 1.2.0

* Import - Amélioration des performances d'imports pour Spatialite
* Import - Ajout d'une option pour activer/désactiver la validation des géométries
* Import - Suppression de l'outil de réparation des multipolygones sur une bdd déja importée (phase de transition terminée )
* Interface - pour l'interface Cadastre, ajout des boutons WMS/WFS - fixes #53
* Export - Debogage des exports PDF vides pour la 2.8 - fixes #60
* Identification parcelle - amélioration interne de l'outil (pas visible dans l'interface)
* Import - Prise en compte des fichiers MAJIC sans contenus dans les premières lignes

## Version 1.1.1

* Ajout de la compatibilité avec QGIS 2.8

## Version 1.1.0

* Options - Ajout du menu Vue/Décorations dans l'interface Cadastre
* Chargement - La couche Unités foncières est décochée par défaut
* Import - Ajout des scripts pyogr pour compatibilité QGIS 2.6
* Ajout d'une boite de dialogue d'information lors du 1er chargement. Visible via le menu Cadastre > Notes de version
* Import/Recherche/Export - Modification du lien entre les parcelles EDIGEO et MAJIC (même identifiant unique pour les 2)
* Import - exhaustivité des données de propriétaire MAJIC - fix #47
* Import - Conserver l'orientation des symboles lors d'imports successifs - fix #46
* Import - Correction des géométries invalides - fix #43
* Import - Correction des multipolygones sous Windows - fixes #44
* Info parcelle - option de filtre commune pour le relevé de propriété - fix #42
* Chargement - Ajout des TRONROUTE_ID pour les étiquettes des noms voies - bug #40
* Chargement - Suppression des étiquettes abbérantes - fix #41
* Import - Ajout des unités foncières pour PostGIS (refonte de la requête)
* Import - MAJIC : ajout de la compatibilité des fichiers 2014
* Import - EDIGEO : ajout de la table boulon_id
* Chargement - correction du bug #38 : minidump sous Windows

## Version 1.0.0

* Import - débogage import PostGreSQL sous Windows
* Recherche - Meilleure gestion de la désactivation des modules de recherche
* Import - MAJIC : possibilité de lancer l'import même si fichiers MAJIC manquants
* Import - Vérifications sur les données MAJIC avant import - bug #37
* Import - Meilleure gestion des chemins des fichiers sources
* Import - Création de bdd spatialite différente selon la version de spatialite - bug #30
* Export - Débogage de l'export PDF pour QGIS 2.4 - bug #36
* Import : MAJIC - arrêt de l'import si aucun fichier trouvé
* Import - Modifications mineures d'interface
* Import - meilleure gestion des imports EDIGEO via ogr2ogr.py au lieu de ogr2ogr.exe (compatibilité MAC + détection des erreurs)


## Version 0.9.9

* Import - correction de certaines erreurs d'import des MULTIPOLYGONES (PostGreSQL et Spatialite)

## Version 0.9.8.1

* Export - debug : suppression des 'print' dans le code

## Version 0.9.8

* Log détaillé : https://github.com/3liz/QgisCadastrePlugin/compare/0.9.7...0.9.8
* Export des relevés - améliorations de mises en forme des données
* Export - propriétaires : ajout de l'époux pour les femmes mariées EX: MME DURAND/Sophie Yvette EP DUPONT Jean
* Export - propriétaires : déplacement des dates et lieu de naissance à droite
* Export - Suppression des zéros au début du numéro de plan et de voirie
* Export - prop. baties : Suppression du code commune au début du numéro INVAR
* Export - Sommes prop. baties : Ajout de zéros si valeurs nulles (au lieu de cases vides)
* Export - prop. non baties : Séparation des HA A CA pour la contenance
* Export - prop. non baties : Calcul de la fraction exo si applicable
* Export - Sommes prop. non baties : Ajout de la somme des contenances
* Export - Pied de page : Ajout de la mention "Ce document est donné à titre indicatif..."
* Export - Suppression de la mention "Expérimental"
* Import - Import des MULTI-POLYGONES et correction de données existantes - bug #29

## Version 0.9.7

* Log détaillé : https://github.com/3liz/QgisCadastrePlugin/compare/0.9.6...0.9.7
* Documentation - ajout des liens vers la documentation en ligne - bug #3
* Export - recupération infos parcelles : ajout du filtre par département - bug #27
* Export - correction du pourcentage exoneration pour les propriétés non baties - bug #26
* Import - validation préalable des entrées du formulaire d'import - bug #25
* Chargement - ajout des chemins SVG cadastre sans écraser les précédents - bug #19
* Identification - debogage outil si Parcelles n'est pas la couche active
* Export - nettoyage du nom du PDF exporté pour compatibilité Windows - bug #23
* Import - sup contrainte de type sur surface des parcelles - bug #20
* Import - suppression de la contrainte de longueur de champ pour l'attribut tex
* Chargement - gestion d'erreur si pas de table trouvée dans la bdd
* Recherche - correction largeur listes déroulantes (windows) - bug #22
* Export - ouverture des PDF compatible freeBSD - bug #21

## Version 0.9.6

* Log détaillé : https://github.com/3liz/QgisCadastrePlugin/compare/0.9.5...0.9.6
* Import - actualisation liste des tar.bz2 après décompression de zip
* Documentation - mise à jour
* Recherche/export - meilleurs résultats si fantoir non importé - bug #18
* Export multiple - barre de progression et ouverture du dossier contenant
* Export - optimisation - bug #2
* Chargement - réutilisation du groupe Cadastre si présent - bug #14
* Identification - réinitialisation de l'outil identifier au chargement
* Spatialite - debogage base de données si chemin contient des espaces - bug #17
* Recherche - adresse/propriétaire : gestion des apostrophes - bug #12
* Import - remplacement CREATE TABLE IF NOT EXISTS - bug #13
* Meilleur comportement des outils de recherche sur ouverture d'un (nouveau) projet

## Version 0.9.5

* Chargement - bug #8: pas d'erreur si présence de couches plugin OpenLayers
* Recherche/Identification - réactivation des outils sur chargement d'un projet Cadastre - #9
* Recherche - Lieux : Liste des sections ordonnées par code
* Import - correction bug Spatialite import relations (*.vec) - bug #7
* Import - Gestion des erreurs de suppression de fichier après extraction - bug #5
* Import - modifications des scripts pour gestion arrondissements (ex: Marseille)

## Version 0.9.4

* Import - bouton Créer une base Spatialite grisé si aucune connection dans QGIS

## Version 0.9.3

* Documentation - ajout d'une documentation (avec copies d'écran)
* Chargement - remplacement du panneau par une fenêtre
* Configurer - ajout d'un option pour le type de stockage temporaire de Spatialite
* Import - spatialite : remove disablespatialindex
* Import - Amélioration des imports consécutifs (indexes, erreurs spatialites, etc.)
* Majic - import récursif
* Général - ajout d'un menu d'aide et rédaction de l'aide
* Import - restriction des imports à 2012 et 2013
* Export - amélioration des calculs des sommes
* A propos - correction coquille
* Recherche/Export - gestion des propriétaires sur plusieurs communes
* About - ajout du lien vers le dépôt Github
* A propos - modification de l'ordre des financeurs

## Version 0.9.2

* Import - suppression des indexes avant ajout Majic incrémental
* Général - rédaction du README et metadata
* Import - amélioration de l'import Spatialite
* A propos - ajout du remerciement aux auteurs d'OpenCadastre
* Général - affichage de la fenêtre 'A propos' à la 1ère utilisation
* Option - ajout de l'aide pour changer d'interface
* Import - amélioration des scripts
* Import - La Direction est bloquée : entier entre 0 et 5
* Chargement - renommage des couches && fermeture des légendes
* Recherche/Identification - désactivation des outils nécessitant MAJIC si pas de données

## Version 0.9.1

* Chargement - ajout du style Orthophoto
* Import - modification interface du choix du type de bdd
* Import - les fichiers EDIGEO non zip/tar.bz2 sont bien pris en compte
* Import - Ajout d'un bouton pour créer une base de données Spatialite vide
* Toolbar - Ajout import/charger/recherche/about + modification icône
* Styles - Classique : amélioration tsurf

## Version 0.9.0

* Correction de régression de 0.8.9 : indentification parcelle et recherche propriétaire

## Version 0.8.9

* Amélioration du support Spatialite : import, recherche, export
* General - désactivation Spatialite si pyspatialite non présent

## Version 0.8.8

* Import - ajout d'une option pour configurer le nombre de ligne INSERT max
* Propriétaires - debug affichage vide pour les personnes morales
* Recherche - ajout des stopwords pour les natvoi
* Indentification parcelle - textes en lecture seule + code section || dnupla
* Import majic - Vérfication unicité des lotslocaux

## Version 0.8.7

* Export - changement du calcul du revenu cadastral non bati + numéro voirie
* Import - possibilité d'importer un fichier MAJIC seul
* Import - Ajout des contraintes à la fin d'un import MAJIC seul
* Import - modification mineure nomenclature EDIGEO
* Import - Compatibilité avec les fichiers MAJIC 2013
* Import MAJIC - ajout de quelques colonnes (bati, nbat)
* Export - Calcul des sommes pour bati et nbat
* Recherche/export - ajout du lieu et date de naissance pour les propriétaires
* Chargement - Création d'un groupe 'Cadastre' et chargement des couches dans ce groupe
* Chargement - mise à jour auto des listes déroulantes suite à un import

## Version 0.8.6

* Recherche/Export - Ajout ccocom dans comptecommunal (dédoublonnage)
* Import - MAJI : suppression des caractères non imprimables et de contrôle

## Version 0.8.5

* Import - debug utilisation mémoire lors de la leture des fichiers majic volumineux
* Recherche - suppression du bug si ouverture panneau avec couches hors cadastre
* Recherche/Indenfitication - Correction du Zoom/Centrer si reprojection à la volée
* Recherche - adaptation remplissage table voie pour gérer le multi-commune

## Version 0.8.4

* Import - Modification dynamique de la projection des tables edigeo
* Recherche - Amélioration recherche d'adresse via table voie (fantoir)
* Chargement - utilisation de Times New Roman pour les étiquettes

## Version 0.8.3

* Import - majic: suppressions de caractères \x00
* Import - debug Windows sur chemins vers scripts contraintes

## Version 0.8.2

* Import - debug du nom du schéma "a" précédemment écrit en dur (régression 0.8.1)
* Import - utilisation du serial pour geo_commune, geo_parcelle et geo_section : évite les erreurs de rétablissement des clés primaires

## Version 0.8.1

* Import - possibilité d'import vers une base de données distante
* Import - possibilité d'importer en plusieurs passes

