# Le taux de boisement en France : évolution par région (2008–2021)

Visualisation de l'évolution du taux de boisement (part du territoire couverte par la forêt) des
régions de France métropolitaine, sur trois campagnes d'inventaire de l'IGN (2008-2012, 2013-2017,
2017-2021). Message : **la forêt gagne du terrain, région par région**. Mise en avant des
progressions les plus marquées (Corse +10 pts, PACA +4 pts) et des régions les mieux boisées
(Bourgogne-Franche-Comté, Auvergne-Rhône-Alpes), avec positionnement de chaque région par rapport
à la moyenne française.

## Lecture

- Chaque courbe est une région ; la ligne **noire en pointillés** est la moyenne France
  métropolitaine, repère pour situer les régions au-dessus / en dessous du niveau national.
- Un tableau de repère montre la progression nationale de longue durée : le taux de boisement passe
  de 26 % (1986) à 31 % aujourd'hui, soit près de 3 millions d'hectares de forêt supplémentaires.
- Taux arrondi au point : les micro-variations (Île-de-France, Occitanie) ne sont pas à
  sur-interpréter ; le signal est la hausse d'ensemble.
- Champ : France métropolitaine (hors DROM) ; le total « France » = métropole.

## Source des données

**IGN**, [Indicateurs de gestion durable des forêts françaises métropolitaines, indicateur 1.1.2](https://foret.ign.fr/IGD/fr/indicateurs/1.1.2)
(surface et taux de boisement par région administrative). Consulté le 1ᵉʳ juillet 2026.
Licence Ouverte / Etalab 2.0 : réutilisation libre, citation IGN obligatoire.

Données extraites et vérifiées dans `data/` (les 4 campagnes disponibles, dont 2006-2009 conservée
en archive même si non tracée) :
- `data/taux_boisement_regions.csv` : taux de boisement (%) par région et période
- `data/surface_foret_regions.csv` : surface de forêt (1000 ha), donnée secondaire plus fine

## Technos

- HTML / CSS / JavaScript
- [Chart.js 4.4](https://www.chartjs.org/)
- Système de Design de l'État ([DSFR](https://www.systeme-de-design.gouv.fr/)) : police Marianne
