# Brief — Dataviz « Le taux de boisement en France »

Fichier de cadrage à déposer dans Claude Code / VS Code pour lancer la construction.

---

## 1. Objectif

Dataviz interactive montrant que **la forêt gagne du terrain en France**, région par région,
sur données **mesurées** par l'inventaire forestier (pas de reconstitution historique).

- Message principal : entre 2006-2009 et 2013-2017, le taux de boisement progresse
  dans quasiment toutes les régions ; à l'échelle nationale, **29 % → 31 %**.
- Angle éditorial : une bonne nouvelle sobre, chiffrée, incontestable.

## 2. Source

- **Producteur :** IGN — Indicateurs de gestion durable des forêts françaises métropolitaines (IGD).
- **Indicateur :** 1.1.2 — Surface et taux de boisement par région administrative.
- **URL :** https://foret.ign.fr/IGD/fr/indicateurs/1.1.2
- **Date de consultation :** 1er juillet 2026
- **Licence :** Licence Ouverte / Etalab 2.0 (réutilisation libre, citation IGN obligatoire).
- **Citation à conserver :** « IGN — Indicateurs de gestion durable des forêts françaises
  métropolitaines, indicateur 1.1.2 ».

## 3. Données (prêtes à versionner)

Champ : France métropolitaine. Périodes = fenêtres glissantes de 5 campagnes d'inventaire.
Taux de boisement exprimé en %.

Format **tidy / long** (recommandé pour la viz) — à enregistrer en
`data/taux_boisement_regions.csv` :

```csv
region,periode,taux_boisement
Île-de-France,2006-2009,22
Île-de-France,2008-2012,21
Île-de-France,2013-2017,23
Centre-Val de Loire,2006-2009,24
Centre-Val de Loire,2008-2012,24
Centre-Val de Loire,2013-2017,25
Bourgogne-Franche-Comté,2006-2009,35
Bourgogne-Franche-Comté,2008-2012,36
Bourgogne-Franche-Comté,2013-2017,36
Normandie,2006-2009,13
Normandie,2008-2012,14
Normandie,2013-2017,14
Hauts-de-France,2006-2009,13
Hauts-de-France,2008-2012,13
Hauts-de-France,2013-2017,14
Grand Est,2006-2009,33
Grand Est,2008-2012,33
Grand Est,2013-2017,34
Pays de la Loire,2006-2009,10
Pays de la Loire,2008-2012,11
Pays de la Loire,2013-2017,12
Bretagne,2006-2009,13
Bretagne,2008-2012,14
Bretagne,2013-2017,15
Nouvelle-Aquitaine,2006-2009,33
Nouvelle-Aquitaine,2008-2012,33
Nouvelle-Aquitaine,2013-2017,34
Occitanie,2006-2009,35
Occitanie,2008-2012,36
Occitanie,2013-2017,35
Auvergne-Rhône-Alpes,2006-2009,34
Auvergne-Rhône-Alpes,2008-2012,35
Auvergne-Rhône-Alpes,2013-2017,36
Provence-Alpes-Côte d'Azur,2006-2009,47
Provence-Alpes-Côte d'Azur,2008-2012,48
Provence-Alpes-Côte d'Azur,2013-2017,51
Corse,2006-2009,54
Corse,2008-2012,56
Corse,2013-2017,62
France,2006-2009,29
France,2008-2012,30
France,2013-2017,31
```

### Donnée secondaire (optionnelle) — surface de forêt (1000 ha)

Plus granulaire que le taux (arrondi à l'entier) ; utile pour une tendance plus fine.
À enregistrer en `data/surface_foret_regions.csv` si besoin.

```csv
region,periode,surface_1000ha
Île-de-France,2006-2009,266
Île-de-France,2008-2012,260
Île-de-France,2013-2017,273
Centre-Val de Loire,2006-2009,937
Centre-Val de Loire,2008-2012,957
Centre-Val de Loire,2013-2017,987
Bourgogne-Franche-Comté,2006-2009,1705
Bourgogne-Franche-Comté,2008-2012,1742
Bourgogne-Franche-Comté,2013-2017,1741
Normandie,2006-2009,390
Normandie,2008-2012,410
Normandie,2013-2017,427
Hauts-de-France,2006-2009,425
Hauts-de-France,2008-2012,430
Hauts-de-France,2013-2017,446
Grand Est,2006-2009,1914
Grand Est,2008-2012,1917
Grand Est,2013-2017,1941
Pays de la Loire,2006-2009,325
Pays de la Loire,2008-2012,351
Pays de la Loire,2013-2017,390
Bretagne,2006-2009,358
Bretagne,2008-2012,386
Bretagne,2013-2017,415
Nouvelle-Aquitaine,2006-2009,2779
Nouvelle-Aquitaine,2008-2012,2827
Nouvelle-Aquitaine,2013-2017,2902
Occitanie,2006-2009,2587
Occitanie,2008-2012,2631
Occitanie,2013-2017,2573
Auvergne-Rhône-Alpes,2006-2009,2424
Auvergne-Rhône-Alpes,2008-2012,2495
Auvergne-Rhône-Alpes,2013-2017,2584
Provence-Alpes-Côte d'Azur,2006-2009,1492
Provence-Alpes-Côte d'Azur,2008-2012,1524
Provence-Alpes-Côte d'Azur,2013-2017,1617
Corse,2006-2009,472
Corse,2008-2012,494
Corse,2013-2017,549
France,2006-2009,16073
France,2008-2012,16419
France,2013-2017,16845
```

## 4. Réserves méthodologiques (à respecter dans la viz)

- **Fenêtres glissantes qui se chevauchent** (2006-2009, 2008-2012, 2013-2017) : deux points
  consécutifs ne sont pas indépendants. Seule la comparaison **2006-2009 → 2013-2017** est
  vraiment robuste. Ne pas suggérer une variation interannuelle fine.
- **Taux arrondi à l'entier** : certaines régions paraissent stagner ou perdre 1 point par simple
  effet d'arrondi (Île-de-France, Occitanie). Ne pas sur-interpréter ces micro-variations ; le
  signal solide est la hausse d'ensemble.
- **Champ : métropole uniquement** (pas de DROM). Le total « France » du tableau = métropole.

## 5. Reproductibilité (si tu veux automatiser le scraping)

La page IGD est un **vrai tableau HTML** → récupérable avec `pandas.read_html(url)` ou BeautifulSoup.
Deux points à gérer :
1. En-tête **multi-niveaux** : 3 périodes × (Forêt / dont forêt de production / Taux de boisement).
2. Colonnes d'**incertitude `±`** intercalées à isoler.
Isoler la colonne « Taux de boisement » de chaque bloc de période, puis passer au format long ci-dessus.
(Les CSV de la section 3 sont déjà extraits et vérifiés : le scraping n'est utile que pour la repro.)

## 6. Spécification de la viz

- **Stack :** Chart.js, standalone HTML/CSS/JS, déployable sur GitHub Pages. Pas de framework lourd.
- **Mobile-first** : la viz est consultée depuis LinkedIn.
- **Un seul message** : « la forêt gagne du terrain, partout ».
- **Piste de forme** (à valider) : slopegraph ou barres groupées, régions triées par taux, France
  mise en évidence. Idéalement, on lit d'un coup d'œil que presque toutes les lignes montent.
- **Interactions** : tooltip région + valeur par période ; survol clair au doigt.
- **À versionner** : le(s) CSV dans `data/`, l'URL source + la date de consultation en commentaire
  du code et dans le README.

---

*Note de cadrage : ce jeu de données est du mesuré (inventaire IGN) et couvre 2006-2017. Il ne
soutient pas le hook « la forêt a doublé depuis 1850 » (qui repose sur des reconstitutions
historiques). Le récit ici est régional et récent : une progression mesurée, homogène, du couvert
forestier.*
