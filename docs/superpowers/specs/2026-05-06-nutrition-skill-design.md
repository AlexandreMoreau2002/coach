# Spec — Skill `/nutrition`

**Date :** 2026-05-06  
**Statut :** Approuvé

---

## Contexte

Alexandre veut sécher (~−5 kg) pour améliorer son ratio force/poids sur l'OAPU. Il ne compte pas ses calories mais réalise que ça va devenir nécessaire. Son alimentation est déjà bien structurée — le problème est qu'il n'a aucune visibilité sur ses apports réels.

---

## Objectif du skill

Skill de nutrition intégré au carnet Obsidian. Deux usages :
1. **Cibles permanentes** — biométrie, macros, règles de calibration
2. **Suivi ponctuel** — log journalier conversationnel, bilan hebdo

---

## Profil nutritionnel d'Alexandre

### Biométrie
- Poids moyen : ~78 kg (moyenne 7 jours : 77,6–78,3 kg)
- Taille : 182 cm
- Âge : 24 ans (né le 24 janvier 2002)
- Morpho : longiligne, ectomorphe, skinny fat historique, un peu sec depuis l'escalade
- Ape index : +9 (envergure 191 cm)
- Appétit : gros, jamais compté, aucune référence de base

### TDEE estimé
- BMR (Mifflin-St Jeor) : `10×78 + 6.25×182 − 5×24 + 5 = 1802 kcal`
- Multiplicateur : 1,45 (desk job sédentaire + 3–5 séances grimpe/semaine)
- **TDEE estimé : ~2600–2800 kcal/jour**
- Calibration : ajuster après 2 semaines de tracking réel

### Cibles journalières (phase sèche)
| | Cible |
|---|---|
| Calories | **2200 kcal** (−400 kcal/jour) |
| Protéines | **175g** (2,25 g/kg) |
| Glucides | **228g** |
| Lipides | **65g** |
| Fibres | **28–32g** |
| Hydratation | **2,7 L/jour** (+500–750 ml/h entraînement) |

### Objectif sèche
- Cible : −5 kg max (78 kg → ~73 kg)
- Rythme attendu : ~0,35 kg/semaine (~3,5 mois)
- Si perte > 0,6 kg/sem → +150 kcal
- Si poids stable après 2 semaines → −150 kcal
- Si ~0,3 kg/sem → ne pas toucher

---

## Alimentation habituelle d'Alexandre

### Rythme
- **Pas de petit-déjeuner** (jeûne intermittent naturel)
- 2 repas principaux : midi + soir
- Snacks pré-entraînement (3×/semaine)

### Base d'aliments connus

| Aliment | Portion | Calories | Protéines | Glucides | Lipides |
|---|---|---|---|---|---|
| Œuf bio moyen | 1 (55g) | 70 kcal | 6g | 0g | 5g |
| Pâtes (sèches) | 100g | 350 kcal | 12g | 72g | 1,5g |
| Raptor Whey Isolate 94% | 30g (1 dose) | 109 kcal | 25g | 1,9g | 0,6g |
| Clif Bar | 1 barre (68g) | 240 kcal | 10g | 44g | 5g |
| Nature Valley Sweet & Salty Peanut | 1 barre | 160 kcal | 3g | 20g | 8g |
| Siggi's Raspberry Skyr | 150g | 110 kcal | 15g | 12g | 0g |
| Yaourt grec nature | 100g | 97 kcal | 9g | 4g | 5g |
| Crème fraîche semi 4% | 100g | 65 kcal | 3g | 4g | 4g |
| Compote pomme-framboise | 100g | 60 kcal | 0g | 14g | 0g |
| Chocolat noir 70% | 20g | 120 kcal | 2g | 8g | 9g |

### Repas types
- **Midi :** 3 œufs + pâtes (200–250g sèches) + source protéine + compote
- **Soir :** 3 œufs + pâtes (200–250g sèches) + source protéine + compote + Siggi's skyr + chocolat 70%
- **Pré-grimpe (3×/sem) :** Clif Bar ou Nature Valley
- **Whey :** 1 dose/jour (timing variable)

### Levier principal identifié
Les pâtes sont l'unique vrai levier calorique variable. La différence entre 175g et 250g sèches par repas = ±260 kcal. Sur 2 repas = ±520 kcal. **Standardiser les pâtes à 175g sèches par repas = première action concrète.**

---

## Micronutriments prioritaires

| Nutriment | Pourquoi | Action |
|---|---|---|
| Collagène + Vit C | Santé tendons/poulies — critique pour la poutre | Bouillon d'os ou supplément 10–15g avant séance doigts |
| Vitamine D3 + K2 | Desk job + Grenoble → probable carence | Supplément 3000 UI D3 / 100 µg K2 le matin |
| Magnésium bisglycinate | Récupération, sommeil | 300–400 mg le soir (à intégrer plus tard) |
| Oméga-3 | Anti-inflammatoire tendineux | Poisson gras 2×/sem ou supplément 2–3g EPA+DHA |
| Zinc | Réparation musculaire | Viande rouge, graines de courge |
| Fer | Oxygénation — surveiller si fatigue | Viande rouge + Vit C pour absorption |

---

## Timing nutrition (jours grimpe)

| Fenêtre | Quoi |
|---|---|
| 1h30–2h avant séance | Glucides lents + protéines légères (~40g C / ~25g P) |
| Dans les 45 min après | Protéines + glucides (~40g P / ~60g C) |
| Distribution protéines | 40–50g par repas × 3–4 repas (MPS optimal) |

---

## Architecture

### Fichiers Obsidian
```
carnet d'entrainement/
├── _nutrition.md              ← profil permanent
└── nutrition/
    └── YYYY-MM-DD.md          ← logs journaliers
```

### Structure log journalier
```markdown
## Repas
- Midi : [description]
- Snack : [description]
- Soir : [description]

## Totaux
Calories : X / 2200 [✓/⚠️]
Protéines : Xg / 175g [✓/⚠️]
Glucides : Xg / 228g [✓/⚠️]
Lipides : Xg / 65g [✓/⚠️]
Fibres : Xg / 30g [✓/⚠️]
```

### Modes du skill

| Invocation | Comportement |
|---|---|
| `/nutrition` | Check-in : demande ce qu'il a mangé → estime macros → écrit le log |
| `/nutrition [description repas]` | Estime les macros → met à jour le log du jour |
| `/nutrition bilan` | Lit les 7 derniers logs → moyenne → compare cibles → ajuste TDEE si 2 semaines |
| `/nutrition [question aliment]` | Répond depuis la base d'aliments connus |

### Intégration `/coach`
Aucune — skills indépendants.

---

## Règles du skill

1. Lire `_nutrition.md` en début de session pour le contexte complet
2. Utiliser la base d'aliments connus pour les estimations (ne pas inventer)
3. Pour les aliments hors base → chercher les valeurs réelles avant d'estimer
4. Toujours afficher le delta restant (ex: "il te reste 45g de protéines")
5. Signal ⚠️ si un macro dépasse +20% ou reste à moins de 70% de la cible en fin de journée
6. Bilan hebdo tous les dimanches si des logs existent
7. Rappeler la règle pâtes si les glucides explosent : "standardise à 175g sèches"
