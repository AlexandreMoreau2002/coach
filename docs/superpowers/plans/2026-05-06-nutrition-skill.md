# Nutrition Skill Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Créer le skill `/nutrition` — profil persistant dans Obsidian + suivi journalier conversationnel + bilan hebdo.

**Architecture:** Un fichier `_nutrition.md` dans le vault Obsidian contient le profil complet d'Alexandre (biométrie, cibles, base d'aliments). Le skill lit ce fichier à chaque invocation, crée/met à jour des logs journaliers dans `nutrition/YYYY-MM-DD.md`, et peut produire un bilan hebdo. Aucune intégration avec `/coach`.

**Tech Stack:** Markdown, Obsidian MCP (`mcp__obsidian-carnet__*`), Write tool en fallback.

---

## Fichiers à créer

| Fichier | Rôle |
|---|---|
| `skills/nutrition/SKILL.md` | Définition du skill — instructions complètes pour Claude |
| `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/_nutrition.md` | Profil nutritionnel permanent d'Alexandre |

---

### Task 1 : Créer `_nutrition.md` dans le vault Obsidian

**Fichiers :**
- Create : `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/_nutrition.md`

- [ ] **Step 1 : Créer le fichier `_nutrition.md`**

Chemin absolu : `/Users/alex/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/_nutrition.md`

Contenu exact :

```markdown
# Nutrition — Profil d'Alexandre

## Biométrie
- Poids courant : 78 kg (moyenne 7 jours au 06/05/2026 : 77,6–78,3 kg)
- Taille : 182 cm
- Âge : 24 ans (né le 24/01/2002)
- Morpho : longiligne, ectomorphe historique, skinny fat → sec depuis escalade

## TDEE estimé
- BMR (Mifflin-St Jeor) : 1802 kcal
- Multiplicateur : 1,45 (desk job + 3–5 séances grimpe/semaine)
- **TDEE estimé : ~2700 kcal/jour**
- Calibration : ajuster toutes les 2 semaines selon évolution du poids

## Cibles journalières — Phase sèche
| | Cible |
|---|---|
| Calories | **2200 kcal** |
| Protéines | **175g** (2,25 g/kg) |
| Glucides | **228g** |
| Lipides | **65g** |
| Fibres | **28–32g** |
| Hydratation | **2,7 L** (+ 500–750 ml/h entraînement) |

## Objectif sèche
- Départ : ~78 kg → Cible : ~73 kg (−5 kg max)
- Rythme attendu : ~0,35 kg/semaine
- Si perte > 0,6 kg/sem → +150 kcal à la cible
- Si poids stable après 2 semaines → −150 kcal à la cible
- Si ~0,3 kg/sem → ne pas toucher

## Rythme alimentaire
- Pas de petit-déjeuner (jeûne naturel)
- 2 repas principaux : midi + soir
- Snacks pré-entraînement 3×/semaine

## Repas types
- **Midi :** 3 œufs bio + pâtes (175g sèches cible, 200–250g habituellement) + source protéine + compote
- **Soir :** 3 œufs bio + pâtes (175g sèches cible) + source protéine + compote + Siggi's skyr + chocolat 70%
- **Pré-grimpe (3×/sem) :** Clif Bar ou Nature Valley Sweet & Salty
- **Whey :** 1 dose Raptor Isolate 94% / jour

## Base d'aliments connus

| Aliment | Portion | Calories | Protéines | Glucides | Lipides | Fibres |
|---|---|---|---|---|---|---|
| Œuf bio moyen | 1 (55g) | 70 kcal | 6g | 0g | 5g | 0g |
| Pâtes (sèches) | 100g | 350 kcal | 12g | 72g | 1,5g | 3g |
| Raptor Whey Isolate 94% | 30g | 109 kcal | 25g | 1,9g | 0,6g | 0,5g |
| Clif Bar | 68g | 240 kcal | 10g | 44g | 5g | 4g |
| Nature Valley Sweet & Salty Peanut | 1 barre (35g) | 160 kcal | 3g | 20g | 8g | 1g |
| Siggi's Raspberry Skyr | 150g | 110 kcal | 15g | 12g | 0g | 0g |
| Yaourt grec nature | 100g | 97 kcal | 9g | 4g | 5g | 0g |
| Crème fraîche semi 4% | 100g | 65 kcal | 3g | 4g | 4g | 0g |
| Compote pomme-framboise | 100g | 60 kcal | 0g | 14g | 0g | 1g |
| Chocolat noir 70% | 20g | 120 kcal | 2g | 8g | 9g | 1g |
| Blanc de poulet | 100g | 110 kcal | 23g | 0g | 2g | 0g |
| Thon en boîte (égoutté) | 100g | 130 kcal | 28g | 0g | 2g | 0g |
| Saumon | 100g | 200 kcal | 20g | 0g | 13g | 0g |
| Steak haché 5% | 100g | 130 kcal | 21g | 0g | 5g | 0g |

## Levier principal
Les pâtes sont l'unique vrai levier calorique variable. **Cible : 175g sèches par repas.** Chaque 25g supplémentaires = +87 kcal.

## Micronutriments prioritaires
- Vitamine D3 + K2 : 3000 UI D3 / 100 µg K2 le matin (probable carence, desk job + Grenoble)
- Collagène hydrolysé + Vit C : 10–15g avant séance poutre/doigts (santé tendons)
- Oméga-3 : 2–3g EPA+DHA/jour ou poisson gras 2×/sem
- Magnésium bisglycinate : 300–400 mg le soir (à intégrer progressivement)

## Timing nutrition — jours grimpe
- 1h30–2h avant : ~40g glucides + ~25g protéines
- < 45 min après : ~40g protéines + ~60g glucides
```

- [ ] **Step 2 : Vérifier que le fichier est bien créé**

```bash
cat "/Users/alex/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/_nutrition.md" | head -20
```

Résultat attendu : les 20 premières lignes du profil.

- [ ] **Step 3 : Committer**

```bash
git add skills/ && git status
```

Note : `_nutrition.md` est dans le vault Obsidian (hors repo git), donc pas à committer.

---

### Task 2 : Créer le skill `skills/nutrition/SKILL.md`

**Fichiers :**
- Create : `skills/nutrition/SKILL.md`

- [ ] **Step 1 : Créer le dossier**

```bash
mkdir -p skills/nutrition
```

- [ ] **Step 2 : Créer `skills/nutrition/SKILL.md`**

Contenu exact :

```markdown
---
name: nutrition
description: Suivi nutritionnel d'Alexandre — check-in journalier, log des repas, bilan hebdo, calcul macros. Lit _nutrition.md pour le profil complet.
---

## Rôle

Tu es le suivi nutritionnel d'Alexandre. Tu connais son profil complet, ses cibles, et sa base d'aliments. Tu logs ses repas, calcules ses macros, et l'alertes quand il dévie de ses cibles.

Ton ton : direct, chiffré, sans bullshit. Pas de morale alimentaire — que des faits.

## Démarrage — toujours lire le profil en premier

Lire `_nutrition.md` dans le vault (`~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/_nutrition.md`) avant toute réponse. Ce fichier contient :
- Biométrie et TDEE actuel
- Cibles journalières
- Base d'aliments connus avec valeurs exactes
- Repas types et levier principal (pâtes)

## Modes d'invocation

### Mode check-in (invocation sans argument)
1. Lire le log du jour (`nutrition/YYYY-MM-DD.md`) s'il existe déjà
2. Demander : "Qu'est-ce que t'as mangé aujourd'hui ?"
3. Calculer les macros depuis la description
4. Afficher un récap rapide avec delta restant
5. Créer ou mettre à jour le log du jour

### Mode log repas (invocation avec description)
`/nutrition [description du repas]`
1. Lire le log du jour s'il existe
2. Calculer les macros du repas décrit
3. Ajouter le repas au log du jour + recalculer les totaux
4. Afficher le récap mis à jour

### Mode bilan (`/nutrition bilan`)
1. Lire les 7 derniers logs journaliers disponibles
2. Calculer : moyenne kcal, protéines, glucides, lipides, fibres
3. Comparer aux cibles
4. Si ≥ 14 jours de données : comparer l'évolution du poids aux apports → ajustement TDEE si nécessaire
5. Identifier le pattern dominant (ex : "tes pâtes du soir dépassent systématiquement")

### Mode question (`/nutrition [question sur un aliment]`)
Répondre depuis la base d'aliments de `_nutrition.md`. Si l'aliment est hors base, chercher les valeurs réelles avant d'estimer.

## Calcul des macros

### Aliments connus
Utiliser exactement les valeurs de la base dans `_nutrition.md`. Ne pas arrondir à la louche.

### Aliments hors base
1. Chercher les valeurs nutritionnelles réelles (ne pas inventer)
2. Ajouter temporairement au calcul
3. Proposer d'ajouter l'aliment à `_nutrition.md` si c'est un récurrent

### Portions non précisées
- "Un repas de pâtes" → demander la quantité sèche (c'est le levier clé)
- "Un steak" → estimer 150g, préciser l'hypothèse
- "Un peu de crème fraîche" → estimer 50g, préciser

## Format du log journalier

Chemin : `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/nutrition/YYYY-MM-DD.md`

```markdown
# Nutrition — JJ/MM/YYYY

## Repas
- **Midi :** [description avec quantités]
- **Snack :** [description]
- **Soir :** [description avec quantités]
- **Whey :** [oui/non]

## Totaux
| | Réalisé | Cible | Delta |
|---|---|---|---|
| Calories | Xkcal | 2200kcal | +/-X |
| Protéines | Xg | 175g | +/-Xg |
| Glucides | Xg | 228g | +/-Xg |
| Lipides | Xg | 65g | +/-Xg |
| Fibres | Xg | 30g | +/-Xg |

## Statut
[✓ Dans les clous / ⚠️ Point(s) à corriger]
[Note courte si ⚠️]
```

## Règles d'alerte (⚠️)

- Calories > 2600 kcal → "Tu dépasses ta maintenance estimée"
- Calories < 1800 kcal → "Déficit trop agressif, risque de catabolisme musculaire"
- Protéines < 140g en fin de journée → "Tu es en dessous du minimum athlète (1,8 g/kg)"
- Glucides > 320g → vérifier les pâtes : "Rappel : cible 175g sèches par repas"
- Fibres < 20g → "Pense aux légumes ou compotes supplémentaires"

## Calibration TDEE (bilan hebdo)

Si ≥ 14 jours de logs :
1. Calculer la moyenne calorique sur la période
2. Comparer à l'évolution du poids (demander le poids actuel si pas connu)
3. Si poids stable à X kcal/jour → X = maintenance réelle → mettre à jour `_nutrition.md`
4. Ajuster la cible en conséquence (-400 kcal de la vraie maintenance)
5. Mettre à jour `_nutrition.md` avec le nouveau TDEE et la nouvelle cible

## Création et mise à jour des logs

**Priorité :** utiliser l'outil Write directement (pas de CLI Obsidian nécessaire).

Chemin absolu : `/Users/alex/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/nutrition/YYYY-MM-DD.md`

Créer le dossier `nutrition/` si inexistant :
```bash
mkdir -p "/Users/alex/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/nutrition"
```

## Frontière médicale

Ce skill suit les apports alimentaires et les macros — pas les pathologies. Si Alexandre mentionne des symptômes inhabituels (fatigue extrême, douleurs digestives récurrentes, etc.) → noter mais orienter vers `Coffre obsidian/santé/` pour le suivi médical.
```

- [ ] **Step 3 : Vérifier la structure**

```bash
cat skills/nutrition/SKILL.md | head -10
```

Résultat attendu : le frontmatter YAML avec `name: nutrition` et `description:`.

- [ ] **Step 4 : Committer**

```bash
git add skills/nutrition/SKILL.md
git commit -m "feat(skill): ajout du skill nutrition

Suivi nutritionnel complet — check-in journalier, log Obsidian,
calcul macros, bilan hebdo et calibration TDEE.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>"
```

---

### Task 3 : Créer le dossier `nutrition/` dans le vault et tester le skill

**Fichiers :**
- Create : `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/nutrition/` (dossier)

- [ ] **Step 1 : Créer le dossier nutrition dans le vault**

```bash
mkdir -p "/Users/alex/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/nutrition"
```

- [ ] **Step 2 : Tester le skill — invocation check-in**

Invoquer `/nutrition` et vérifier que le skill :
1. Lit `_nutrition.md` correctement (biométrie, cibles)
2. Demande ce qu'Alexandre a mangé
3. Calcule les macros d'un repas test ("3 œufs + 175g pâtes sèches + 150g poulet + compote")
4. Crée le fichier `nutrition/2026-05-06.md` avec le bon format

Résultat attendu :
```
Midi estimé :
- 3 œufs : 210 kcal / 18g P / 0g C / 15g L
- 175g pâtes sèches : 612 kcal / 21g P / 126g C / 2,6g L
- 150g poulet : 165 kcal / 34g P / 0g C / 3g L
- Compote 100g : 60 kcal / 0g P / 14g C / 0g L
Total midi : 1047 kcal / 73g P / 140g C / 20,6g L
Restant : 1153 kcal / 102g P / 88g C / 44g L
```

- [ ] **Step 3 : Vérifier le fichier log créé**

```bash
cat "/Users/alex/Library/Mobile Documents/iCloud~md~obsidian/Documents/carnet d'entrainement/nutrition/2026-05-06.md"
```

Résultat attendu : fichier avec la section `## Repas` et `## Totaux` bien formatés.

- [ ] **Step 4 : Sauvegarder le profil en mémoire**

Écrire dans la mémoire du projet : biométrie d'Alexandre, cibles macros, alimentation type — pour que les futures sessions aient le contexte sans relire `_nutrition.md` à chaque fois.
```
