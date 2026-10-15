# FORFIRE-AI — Challenge Data Science

**Prédiction du Risque d'Incendie de Forêt
à partir de Données Satellitaires**

## Objectif

Prédire le **Fire Ignition Index (FII)**, un
indicateur de risque d'incendie normalisé dans
[0, 1], à partir de 16 variables environnementales
issues de trois sources satellitaires libres :
Sentinel-2, SRTM et ERA5.

**Type de problème** : Régression supervisée
**Métrique principale** : R²

## Fichiers fournis
1/ |`data/train.csv` | Données d'entraînement avec `fire_risk` |[⬇️ Télécharger](https://github.com/saracharrada/FORFIRE-AI-Challenge/releases/tag/v1.0.0)
2/ |`data/validation.csv` | Données de validation avec `fire_risk` | 
3/ |`data/test.csv` | Données de test **SANS** `fire_risk` |
4/ |`data/README.txt` | Description complète des variables |

⚠️ Ces données sont **strictement confidentielles**.
Elles ne doivent pas être partagées, redistribuées
ou publiées en dehors de ce challenge.

---

## Dates importantes

- Mise à disposition du dataset | 16/10/2026 |
- Date limite de soumission | 15/11/2026 |
- Annonce des résultats | 25/11/2026 |

---

## Comment soumettre

1. **Forkez** ce dépôt
2. Créez le dossier `submissions/NomEquipe/`
3. Ajoutez votre fichier `submission.csv`
5. Ouvrez une **Pull Request** avec le titre :
   `[SOUMISSION] NomEquipe — R²=0.XXX`

### Format du fichier de soumission

```csv
obs_id,fire_risk
20200818_0387_0982,0.6234
20200823_0100_0500,0.7891
```

- Exactement **100 000 lignes**
- Même ordre que `test.csv`
- Valeurs `fire_risk` dans [0, 1]

---

## Contact
Sara Charrada —
charradasarra@eniso.u-sousse.tn — Université de Sousse
