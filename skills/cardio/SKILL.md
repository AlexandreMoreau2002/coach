---
name: cardio
description: Analyse une sortie cardio d'Alexandre (course, trail, marche active) à partir d'un export Garmin/Komoot. Produit une analyse orientée grimpeur — pas d'objectif compétitif, focus récupération active, aérobie de base et gestion de l'effort.
---

Arguments attendus : fichier(s) d'activité fournis par Alexandre (FIT, GPX, CSV Garmin Connect, ou copie texte des stats)

## Contexte d'Alexandre

- Grimpeur principal, le cardio est **complémentaire** — pas de compétition running
- Objectif cardio : aérobie de base, récupération active, sortie plaisir
- Montre : Garmin Fenix 8
- Apps : Garmin Connect, Komoot
- Pas de cardio structuré → ne pas prescrire des zones complexes d'emblée

---

## Formats acceptés — par ordre de richesse de données

### 1. Fichier FIT (recommandé)
Export depuis Garmin Connect → Activité → `···` → **Exporter au format FIT original**
Contient : GPS, FC (fréquence cardiaque), allure, cadence de pas, altitude, variabilité FC (HRV si activée), VO2max estimée.

**Comment le lire** :
```bash
# Avec python-fitparse (si installé)
pip install fitparse
python3 -c "
from fitparse import FitFile
fit = FitFile('activity.fit')
for record in fit.get_messages('record'):
    print({d.name: d.value for d in record})
"
```

### 2. Fichier GPX
Export depuis Garmin Connect ou Komoot → contient GPS + altitude + timestamps.
**Pas de données FC** sauf si la montre les a intégrées dans les extensions GPX.

**Comment le lire** : c'est du XML — le lire directement avec l'outil Read.

### 3. CSV Garmin Connect (laps / splits)
Export depuis Garmin Connect → vue détaillée → **Exporter CSV**
Contient : allure par km, FC moy/max par km, altitude gagnée par km.

**Comment le lire** : lire directement avec l'outil Read ou Bash.

### 4. Screenshot ou copie texte des stats
Garmin Connect → résumé de l'activité → copier les métriques visibles.
Minimum utilisable : distance, durée, FC moy, FC max, dénivelé +/-, allure moy.

---

## Analyse à produire

### A — Données brutes (synthèse)
- Distance, durée, dénivelé +/- 
- Allure moyenne et allure sur les segments clés
- FC moyenne, FC max, temps en zones (si disponible)
- Cadence moyenne (si disponible)

### B — Lecture orientée grimpeur
1. **Intensité réelle** — était-ce récupératif (Z1-Z2), modéré (Z3) ou dur (Z4+) ?
2. **Dénivelé vs FC** — la montée a-t-elle provoqué une dérive cardiaque ? Signe de manque d'aérobie de base ou de fatigue résiduelle
3. **Gestion de l'effort** — allure stable, positive split (départ trop vite) ou negative split (bien géré) ?
4. **Impact sur la récup escalade** — une sortie Z1-Z2 aide la récupération musculaire ; une sortie Z4+ la compromet

### C — Recommandation courte
- Cette sortie était-elle cohérente avec le cycle grimpe en cours ?
- Faut-il ajuster la prochaine sortie cardio (plus court, moins intense, plus de dénivelé) ?
- Signaler si la FC de repos post-sortie est élevée (signe de fatigue systémique)

---

## Enregistrement dans le carnet Obsidian

Créer le fichier : `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/YYYY/Mois/JJ.MM.YYYY - cardio.md`

### Format cardio

```markdown
# Cardio — [type : course / trail / marche] ~[durée]

---

Départ : ___  |  Arrivée : ___

---

### Stats clés

- Distance : ___ km
- Durée : ___
- Dénivelé : +___ m / -___ m
- Allure moy : ___ /km
- FC moy : ___ bpm  |  FC max : ___ bpm
- Zones FC : Z1 ___% | Z2 ___% | Z3 ___% | Z4+ ___%

---

### Lecture coach

> [intensité réelle — 1 phrase]
> [impact récup grimpe — 1 phrase]
> [point à retenir pour la prochaine sortie]

---

#cardio #[course|trail|marche]
```

---

## Workflow d'exécution

1. **Identifier le format** fourni par Alexandre (FIT / GPX / CSV / texte)
2. **Extraire les métriques** avec l'outil approprié (Read pour GPX/CSV, Bash + fitparse pour FIT)
3. **Calculer les zones FC** si les données brutes sont disponibles (zones Garmin par défaut : Z1<50%, Z2 50-60%, Z3 60-70%, Z4 70-80%, Z5>80% de FC max)
4. **Produire l'analyse** en 3 blocs (données, lecture, recommandation)
5. **Créer le fichier Obsidian** au format cardio
6. Ouvrir dans Obsidian :
```bash
open "obsidian://open?vault=carnet%20d'entrainement&file=[chemin encodé URL]"
```
