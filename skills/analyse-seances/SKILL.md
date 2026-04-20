---
name: analyse-seances
description: Analyse le carnet d'entraînement Obsidian d'Alexandre et retourne un résumé structuré des performances récentes, tendances et points faibles. Lit aussi _profil.md et _programme.md pour contextualiser.
---

## Chemins du carnet

Racine : `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/`

Lire dans cet ordre :
1. `_profil.md` — contexte permanent d'Alexandre
2. `_programme.md` — cycle et objectifs en cours
3. Tous les fichiers `.md` dans `YYYY/Mois/` — séances datées

## 1. Performances récentes (5 dernières séances)
- Date, type de séance, exercices, charges/reps notés

## 2. PRs identifiés
- Par exercice : meilleure charge, meilleur volume

## 3. Tendances
- Fréquence d'entraînement
- Exercices récurrents vs abandonnés
- Progression ou stagnation par exercice

## 4. Points faibles identifiés
- Exercices où la progression est lente ou absente
- Zones corporelles peu travaillées

## 5. Profil synthétique
- Rappel des objectifs depuis `_profil.md`
- Cohérence entre programme actuel (`_programme.md`) et séances réelles

Retourne ce résumé de façon concise pour que le skill `coach` puisse s'en servir pour le check-in et la planification de séance.
