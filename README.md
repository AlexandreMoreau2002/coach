# Coach — Plugin d'entraînement personnel

Plugin Claude Code pour Alexandre Moreau.
Versionné dans [github.com/AlexandreMoreau2002/config](https://github.com/AlexandreMoreau2002/config).

---

## Ce que c'est

Un assistant coach personnel qui connaît ton profil, lit ton carnet d'entraînement Obsidian et t'aide à planifier tes séances. Il démarre toujours par un check-in rapide pour adapter ses propositions à ton état du jour.

---

## Installation

Depuis la racine du config repo :

```bash
claude plugins install ./coach
```

Pour vérifier que le plugin est actif :

```bash
claude plugins list
```

Le plugin apparaît sous le nom `coach@local`. Redémarre Claude Code si les skills ne sont pas disponibles immédiatement.

---

## Comment l'utiliser

### Depuis n'importe où

```
/coach
```

Le coach te demande comment tu vas, puis propose de :
- **Créer une séance** adaptée à ton état du jour
- **Réfléchir sur un thème** (technique, exercice, méthode)
- **Revoir ta planification** (cycle, semaine, objectifs)

### Depuis ton carnet Obsidian

Ouvre une conversation Claude dans le dossier du carnet — le `CLAUDE.md` déclenche `/coach` automatiquement.

---

## Skills inclus

| Skill | Rôle |
|-------|------|
| `coach` | Point d'entrée — check-in + routing |
| `seance` | Crée les fichiers de séance Obsidian au bon format |
| `analyse-seances` | Lit et résume les 5 dernières séances du carnet |
| `methodes` | Knowledge base des techniques d'entraînement |
| `recherche` | Recherche scientifique validée (WebSearch) |

---

## Structure du carnet Obsidian

```
carnet d'entrainement/
├── CLAUDE.md              ← auto-déclenche /coach
├── _profil.md             ← ton profil permanent (modifie si tes objectifs changent)
├── _programme.md          ← ton cycle actuel (mis à jour au fil des semaines)
├── _templates/
│   ├── force.md
│   ├── grimpe.md
│   └── polyvalent.md
└── YYYY/Mois/JJ.MM.YYYY - [type].md
```

Les fichiers préfixés `_` sont toujours lus en premier par le coach.

---

## Mise à jour des skills

Édite directement les fichiers dans `coach/skills/`, puis committe dans le config repo. Aucune réinstallation nécessaire — le cache se met à jour automatiquement.
