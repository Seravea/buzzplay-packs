# 🎵 BuzzPlay — Packs de quiz

Catalogue **public** des packs de quiz BuzzPlay. L'app le télécharge **automatiquement à chaque lancement** (silencieux, puis cache local hors-ligne) : **modifier ce fichier suffit**, aucune mise à jour de l'app n'est nécessaire.

## ➕ Ajouter un quiz / un pack

1. Éditer [`quiz_packs.json`](quiz_packs.json) (directement sur GitHub : ✏️ Edit).
2. Ajouter un objet dans `"packs"` (ou un set dans un pack existant) :

```json
{
  "id": "pack-noel-2026",
  "title": "Spécial Noël",
  "iconName": "snowflake",
  "category": "special",
  "sets": [
    {
      "id": "noel-classiques",
      "title": "Chansons de Noël",
      "questions": [
        {
          "question": "Qui chante « All I Want for Christmas Is You » ?",
          "answers": ["Mariah Carey"],
          "difficulty": "facile",
          "funFact": null
        }
      ]
    }
  ]
}
```

3. Commit → le pack apparaît dans l'app au prochain lancement, section **« Packs bonus »**.

## 🆓 Gratuit ou 🔒 premium ?

- **Sans `productID`** → pack **gratuit**, jouable immédiatement.
- **Avec `productID` + `priceDisplay`** → pack **premium** : cadenas + prix, achat dans l'app.

```json
"productID": "buzzplay.quiz.noel",
"priceDisplay": "0,99 €",
```

⚠️ Pour un pack premium **réel**, le `productID` doit exister dans App Store Connect (produit Non-Consumable). Tant que StoreKit est en mock, n'importe quel `productID` fonctionne en test.

## 📋 Règles

| Champ | Valeurs |
|---|---|
| `id` (pack & set) | unique et **stable** (ne jamais le changer après publication) |
| `iconName` | un SF Symbol valide (vérifier dans l'app SF Symbols) |
| `category` | `era` (bleu) · `genre` (violet) · `special` (jaune) |
| `difficulty` | `facile` · `moyen` · `difficile` · `expert` |
| `answers` | liste des réponses acceptées (la 1ʳᵉ est affichée) |
| `funFact` | optionnel (`null` ok) — affiché après la réponse |

Erreur de JSON ? L'app **ignore silencieusement** le fichier et garde son cache : valider sur [jsonlint.com](https://jsonlint.com) avant de committer.
