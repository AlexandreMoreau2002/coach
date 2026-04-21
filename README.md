# Coach - Plugin d'entrainement personnel

Plugin Claude Code et Codex pour Alexandre Moreau.
Versionne dans [github.com/AlexandreMoreau2002/coach](https://github.com/AlexandreMoreau2002/coach).

---

## Ce que c'est

Un assistant coach personnel qui connait ton profil, lit ton carnet d'entrainement Obsidian et t'aide a planifier tes seances. Il demarre toujours par un check-in rapide pour adapter ses propositions a ton etat du jour.

---

## Installation

### Claude Code

```bash
claude plugins marketplace add AlexandreMoreau2002/coach
claude plugins install coach
```

### Codex

```bash
codex plugin marketplace add AlexandreMoreau2002/coach
```

Puis redemarre Codex. Le plugin expose ses skills via `.codex-plugin/plugin.json`.

Fallback manuel si la commande marketplace n'est pas disponible sur une vieille version de Codex :

```bash
git clone https://github.com/AlexandreMoreau2002/coach ~/.codex/coach
mkdir -p ~/.agents/skills
ln -sfn ~/.codex/coach/skills ~/.agents/skills/coach
```

---

## Comment l'utiliser

### Depuis n'importe où

Dans Claude Code :

```text
/coach
```

Dans Codex CLI, les slash commands custom de plugins ne sont pas exposees dans le popup `/` pour l'instant. Appelle le skill en langage naturel :

```text
coach
```

ou :

```text
Lance mon coach d'entrainement.
```

Le coach te demande comment tu vas, puis propose de :
- **Creer une seance** adaptee a ton etat du jour
- **Reflechir sur un theme** (technique, exercice, methode)
- **Revoir ta planification** (cycle, semaine, objectifs)

### Depuis ton carnet Obsidian

Ouvre une conversation Claude dans le dossier du carnet : le `CLAUDE.md` declenche `/coach` automatiquement.

---

## Skills inclus

| Skill | Rôle |
|-------|------|
| `coach` | Point d'entree - check-in + routing |
| `seance` | Cree les fichiers de seance Obsidian au bon format |
| `analyse-seances` | Lit et resume les 5 dernieres seances du carnet |
| `methodes` | Knowledge base des techniques d'entraînement |
| `recherche` | Recherche scientifique validee (WebSearch) |

---

## Structure du carnet Obsidian

```
carnet d'entrainement/
|-- CLAUDE.md              # auto-declenche /coach
|-- _profil.md             # ton profil permanent
|-- _programme.md          # ton cycle actuel
|-- _templates/
|   |-- force.md
|   |-- grimpe.md
|   `-- polyvalent.md
`-- YYYY/Mois/JJ.MM.YYYY - [type].md
```

Les fichiers prefixes `_` sont toujours lus en premier par le coach.

---

## Mise à jour des skills

Edite directement les fichiers dans `coach/skills/`, puis committe dans ce repo. Aucune reinstallation n'est necessaire pour une installation locale : le cache se met a jour au redemarrage de l'app.
