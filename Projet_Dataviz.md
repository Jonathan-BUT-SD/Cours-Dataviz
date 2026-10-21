# Les sorties de jeux sur Steam - dashboard interactif

**Jonathan FONTANA** - BUT Science des Données, 3e année, formation en alternance (SD 3A FA)
Projet individuel de data visualisation - thématique « Les jeux vidéo » - outil : **Streamlit & Python**

![Capture d'écran du dashboard](images/dashboard.png)

## Le projet

Chaque jour, des dizaines de jeux sortent sur Steam, la plus grande boutique de jeux PC. Ce dashboard
montre **quand**, **combien** et **à quel prix** : il suit les sorties jour par jour sur une année
(2023 par défaut), repère les périodes creuses et les records, et met en avant les jeux qui ont le
plus fait réagir les joueurs.

En 2023, **15 030 jeux** sont sortis sur Steam (41 par jour, +20 % par rapport à 2022). Trois constats ressortent :

- **Les sorties se font en semaine** : 51 jeux par jour du lundi au vendredi contre 16 le week-end ;
  le jeudi et le vendredi concentrent à eux seuls 43 % des sorties.
- **Les soldes Steam font chuter le rythme** : -29 % pendant les soldes d'été, -24 % pendant celles
  d'automne. Le record de l'année (99 jeux) tombe le vendredi 1er décembre, juste après les soldes d'automne.
- **Les jeux sont plutôt bon marché** : la moitié des jeux payants coûtent moins de 5,89 € et 73 %
  moins de 10 €. Et un prix plus élevé ne garantit pas une meilleure note : sur les 1 707 jeux d'au
  moins 200 avis, le lien entre prix et part d'avis positifs est faible (corrélation de rang : -0,11).

## Les visualisations

| Visualisation | Type de graphique | Ce qu'elle montre |
|---|---|---|
| Indicateurs clés + « À retenir » | Cartes KPI et encadrés de synthèse | Total, moyenne par jour, semaine vs week-end, records, et trois constats recalculés selon les filtres |
| Le rythme de l'année | Nuage de points journalier + courbe en aire (moyenne glissante 7 jours), annotations | Le rythme quotidien, les creux pendant les soldes Steam, le record |
| Mois par mois | Diagramme en barres | Les mois les plus chargés (octobre en tête) |
| Le calendrier | Calendrier en carte de chaleur (une case par jour) | Les lignes du jeudi et du vendredi ressortent toute l'année |
| Combien coûtent-ils ? | Histogramme par tranches de prix | La répartition des prix, avec le prix médian |
| Les 10 jeux les plus commentés | Graphique en sucettes (lollipop) | Les jeux phares de l'année et leur part d'avis positifs |
| Le prix fait-il la note ? | Nuage de points (taille = nombre d'avis) | Le lien entre prix et avis positifs, avec la corrélation de rang |

Le dashboard utilise un thème sombre avec deux couleurs seulement : le bleu pour les données et
l'orange pour mettre en avant une valeur (mois record, tranche de prix la plus fréquente, jeu le plus
commenté). Ce couple de couleurs a été vérifié pour la lisibilité sur fond sombre et pour les personnes daltoniennes.

## Interactivité

- **Filtres** en haut de page : année (2014 à 2023), genre (Action, Indépendant, Course…) et prix
  (gratuits / payants). Tous les graphiques, indicateurs et le texte de synthèse se recalculent.
- **Infobulles** au survol de chaque barre, cellule ou point.
- **Vue tableau** dépliable avec la liste des jeux de la sélection.

## Les données

- Source : [Steam Catalog Insights (octobre 2024)](https://github.com/NewbieIndieGameDev/steam-insights),
  export d'une base construite à partir de l'API Steam et de SteamSpy.
- 76 916 jeux sortis entre 2013 et 2023 (les démos sont exclues), avec date de sortie, prix,
  genres et nombre d'avis.
- `prepare_data.py` télécharge les tables brutes, les nettoie et les joint dans `data/steam_games.csv`.
- Dates des soldes Steam 2023 : annonces officielles de Valve.

**Limites** : seuls les jeux encore en vente en octobre 2024 sont comptés (les jeux retirés depuis
n'apparaissent pas). Les prix sont les prix de base en euros relevés en octobre 2024 et les avis
sont cumulés jusqu'à cette date.

## Lancer le dashboard

```bash
pip install -r requirements.txt
streamlit run app.py
```

Pour régénérer les données à partir de la source : `python prepare_data.py`.

## Structure du dépôt

```
├── app.py                 # le dashboard Streamlit
├── prepare_data.py        # téléchargement et nettoyage des données
├── data/steam_games.csv   # données prêtes à l'emploi
├── images/dashboard.png   # capture d'écran
├── requirements.txt
└── .streamlit/config.toml # thème sombre du dashboard
```
