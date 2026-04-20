---
name: seance
description: Crée un fichier de séance dans le carnet Obsidian d'Alexandre au bon format, avec checkboxes cochables, temps de repos, et techniques d'intensification si pertinent.
---

Arguments attendus : type de séance, durée, date (optionnelle — aujourd'hui par défaut)

## Règles de format

- Fichier créé dans : `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/YYYY/Mois/JJ.MM.YYYY - [type].md`
- Les mois en français avec majuscule (Janvier, Février, Mars, Avril, Mai, Juin, Juillet, Août, Septembre, Octobre, Novembre, Décembre)
- Checkboxes Obsidian : `- [ ]` uniquement (pas de listes numérotées)
- Blancs à remplir : `___`
- Temps de repos indiqué sur chaque bloc avec une note sur pourquoi (frais ou enchaîner)
- Début/fin de séance : deux lignes vides à remplir en haut
- Maximum 4-5 exercices
- Durée respectée strictement

## Structure type

```
# [Type] — [Thématique] ~[durée]

---

Début de séance à ___
Fin de séance à ___

---

### [Exercice] — [durée bloc]
> repos [X] min — [raison courte]

#tag — [info max ou charge]

- [ ] S1 — ___ rep à ___ kg
- [ ] S2 — ...
```

## Ordre des blocs

1. Exercice technique/neural en premier (frais)
2. Force max ensuite
3. Complémentaires en finition (peuvent enchaîner)

## Création du fichier

Utiliser l'Obsidian CLI en priorité — crée le dossier, indexe la note et l'ouvre en une commande :

```bash
obsidian vault="carnet d'entrainement" create path="YYYY/Mois/JJ.MM.YYYY - [type].md" content="[contenu]"
```

Si `obsidian` n'est pas dans le PATH, essayer le binaire directement :
```bash
/Applications/Obsidian.app/Contents/MacOS/Obsidian vault="carnet d'entrainement" create path="..." content="..."
```

> Note : le CLI doit être activé dans Obsidian → Paramètres → Général → Avancé.

**Fallback** si le CLI n'est pas disponible :
1. Créer le dossier si inexistant
2. Écrire le fichier via l'outil `Write` : `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/YYYY/Mois/JJ.MM.YYYY - [type].md`
3. Ouvrir dans Obsidian :
```bash
open "obsidian://open?vault=carnet%20d'entrainement&file=[chemin encodé URL]"
```
