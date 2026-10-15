
================================================================
FORFIRE-AI CHALLENGE — Prédiction du Risque d'Incendie a partir 
des données sattelites 
Equipe Projet : Sara CHARRADA (ENISo)
		Mehrez ABDELLAOUI (ENISo)
		Ali DOUIK (ENISo)
Date : 25 Septembre 2026.
================================================================

================================================================
OBJECTIF
================================================================
Prédire le Fire Ignition Index (fire_risk), un indice
normalisé de risque d'incendie dans [0, 1].

Type de problème : RÉGRESSION supervisée

Métrique principale  : R²  (à maximiser)
Métriques secondaires: RMSE, MAE (à minimiser)

================================================================
FICHIERS FOURNIS
================================================================
train.csv      → 816,195 lignes — avec fire_risk
validation.csv → 99,899 lignes — avec fire_risk
test.csv       → 99,899 lignes  — SANS fire_risk

⚠️  train.csv et validation.csv contiennent
    intentionnellement des imperfections.
    Un travail de data cleaning est OBLIGATOIRE.
    test.csv est propre.

================================================================
IDENTIFIANT UNIQUE
================================================================
Chaque observation possède un identifiant unique :
  obs_id : format YYYYMMDD_RRRR_CCCC
           YYYYMMDD = date d'acquisition
           RRRR     = indice ligne (row)
           CCCC     = indice colonne (col)

Exemple : 20200729_0387_0982
→ Pixel (387, 982) au 29 juillet 2020

⚠️  Le fichier de soumission doit contenir
    obs_id et fire_risk dans le même ordre
    que test.csv.

================================================================
DESCRIPTION DES COLONNES
================================================================

IDENTIFIANT :
  obs_id        Identifiant unique par observation
                Format : YYYYMMDD_RRRR_CCCC
                Stable et unique dans tout le dataset

LOCALISATION :
  date          Date Sentinel-2 (YYYY-MM-DD)
                15 dates de 2020-05-05 à 2020-08-28
  row           Indice ligne pixel (0 à 593)
  col           Indice colonne pixel (0 à 1291)
  latitude      Latitude WGS84 (°N)
  longitude     Longitude WGS84 (°E)

DONNEES SPECTRALES (Sentinel-2 L2A, 10m) :
  NDVI          [-1, +1] — indice de végétation
  NDMI          [-1, +1] — indice d'humidité combustible
  NBR           [-1, +1] — indice de brûlure

DONNEES TOPOGRAPHIQUES (SRTM, statiques) :
  altitude      [21, 49] m
  pente         [0, 19.84] °
  orientation        [0, 360] °

DONNEES MÉTÉOROLOGIQUES (ERA5, 10h UTC) :
  t2m_C         [20.8, 30.8] °C
  RH            [47.5, 85.6] %
  wind_speed    [0.83, 9.56] m/s
  wind_dir      [0, 360] °
  tp            = 0 partout (saison sèche)

COLONNE PARASITE (à ignorer) :
  id_observation  Identifiant interne — aucune valeur

CIBLE :
  fire_risk     [0, 1] — Fire Ignition Index

================================================================
IMPERFECTIONS INTENTIONNELLES (train + validation)
================================================================
Le challenge teste votre capacité à :
  1. Identifier et traiter les données imparfaites
  2. Construire un modèle robuste sur données propres

Imperfections présentes :
  ① Valeurs manquantes (NaN)
     Colonnes concernées : NDVI, NDMI, t2m_C,
     RH, wind_speed, slope

  ② Doublons
     Lignes dupliquées dans train.csv

  ③ Outliers (valeurs hors plage physique)
     Colonnes concernées : NDVI, t2m_C,
     wind_speed, altitude

  ④ Erreurs de type de données dans quelques colonnes

  ⑤ Colonne parasite
     id_observation : à ignorer

================================================================
FORMAT DE SOUMISSION
================================================================
Fichier nommé : submission_[NomEquipe].csv

Contenu requis :
  - Colonne obs_id (copier depuis test.csv)
  - Colonne fire_risk (prédictions du modèle développé)
  - Même nombre de lignes que test.csv
  - Même ordre que test.csv
  - Valeurs fire_risk dans [0, 1]

Exemple :
  obs_id,fire_risk
  20200818_0387_0982,0.6234
  20200823_0100_0500,0.7891
  20200828_0250_0750,0.4523


