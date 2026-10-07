# Le vélo à Paris en 2025

**Jonathan FONTANA · Salma KOULIJ-CHAABAN**
BUT Science des Données - 3e année, formation en alternance (SD 3A FA)

![Le vélo à Paris en 2025](b642aaef-53d3-4388-b981-9db9f3d85290.png)

## Ce que racontent les données

En 2025, les compteurs parisiens ont enregistré **81 millions de passages de vélos**. Le vélo sert d'abord à aller travailler : on compte **48 % de passages en plus en semaine** que le week-end, avec deux pointes très nettes à **8h et 18h**. La fréquentation suit le rythme de l'année : elle culmine en **juin et septembre**, recule en **août (-19 %)** et s'effondre à Noël. Le **18 septembre**, jour de grève dans les transports, beaucoup de Parisiens ont pris le vélo : c'est le **record de l'année (414 494 passages)**, près de deux fois un jour moyen.

## Chiffres clés

| Indicateur | Valeur |
|---|---|
| Passages comptés en 2025 | 81 312 400 |
| Moyenne par jour | 222 774 |
| Moyenne par jour en semaine / le week-end | 245 544 / 165 630 |
| Jour record | jeudi 18 septembre 2025 (414 494) |
| Jour le plus calme | jeudi 25 décembre 2025 (50 190) |
| Compteurs | 122 compteurs sur 85 sites |

## Les graphiques

- **Chaque jour de l'année** : total des passages par jour et moyenne glissante sur 7 jours.
- **Mois par mois** : total mensuel, en millions de passages.
- **Quand roule-t-on ?** : passages moyens par heure et par jour de la semaine.
- **Une journée type** : profil horaire, semaine et week-end.
- **Les 10 sites les plus fréquentés** : total de l'année, deux sens de circulation additionnés.

## Données

Source : Ville de Paris - [Comptage vélo - Historique - Données Compteurs et Sites de comptage](https://opendata.paris.fr/explore/dataset/comptage-velo-historique-donnees-compteurs/), opendata.paris.fr (licence ODbL).

Fichier utilisé : `2025-comptage-velo-donnees-compteurs.csv` (1,9 Go, environ 1,5 million de relevés horaires). Les compteurs ne comptent que les vélos (pas les trottinettes). Un compteur en panne peut faire baisser ponctuellement les totaux.

## Refaire l'image

```bash
pip install pandas matplotlib
python affiche_velo_paris.py 2025-comptage-velo-donnees-compteurs.zip --sortie Velo_Paris_2025.png
```

Le script lit le fichier par morceaux (il fonctionne même avec plusieurs Go de données) et produit une image PNG. Option `--annee 2024` pour une autre année.
