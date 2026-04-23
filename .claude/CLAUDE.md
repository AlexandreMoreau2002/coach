# Coach — Carnet d'entraînement d'Alexandre

## Vault Obsidian
Path: /Users/alex/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement

Ce coffre est le carnet d'entraînement persistant d'Alexandre.

### Lire dans cet ordre (contexte minimum avant toute séance)
1. `_profil.md` — profil permanent (niveau, objectifs, matériel)
2. `_programme.md` — cycle et objectifs en cours
3. `YYYY/Mois/*.md` — 3 à 5 dernières séances pour la progression

### Structure du vault
```
carnet d'entrainement/
├── _profil.md          # profil permanent
├── _programme.md       # cycle actif
├── _notes/             # notes libres
├── _templates/         # templates de séance
├── 2024/Mois/          # séances 2024
└── 2026/Mois/          # séances 2026
```

### Conventions de fichiers
- Séances : `JJ.MM.YYYY - type de séance.md`
- Le skill `/seance` crée les fichiers au bon format automatiquement
- Le skill `/analyse-seances` lit le vault et retourne les tendances

## Skills disponibles
- `/coach` — point d'entrée principal, check-in + proposition de séance
- `/seance` — crée un fichier de séance dans le vault
- `/analyse-seances` — analyse les performances récentes
- `/recherche` — recherche sur les meilleures pratiques (web)
- `/methodes` — référentiel des techniques d'intensification
