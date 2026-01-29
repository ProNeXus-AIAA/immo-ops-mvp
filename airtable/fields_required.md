# Champs W1 - Génération d'annonce IA

Base : `appnfgRjmtfHz73xt`
Table : `Biens`

## Champs à créer

| Nom du champ | Type | Description |
|--------------|------|-------------|
| Générer annonce | Checkbox | Déclenche la génération IA |
| Annonce IA | Long text | Contenu de l'annonce générée |
| Annonce générée le | DateTime | Horodatage de la génération |
| Brief annonce | Long text | Instructions/contexte pour l'IA |
| Prompt version | Single line text | Version du prompt utilisé |
| Erreur annonce | Long text | Message d'erreur si échec |

## Vue à créer

**Nom** : `🧠 W1 — à générer`
**Type** : Grid (tableur)

**Filtres** :
- `Générer annonce` = checked (coché)
- `Annonce générée le` is empty (vide)

## Commandes API (référence)

```bash
# Créer un champ (exemple)
curl -X POST "https://api.airtable.com/v0/meta/bases/appnfgRjmtfHz73xt/tables/Biens/fields" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"name": "Générer annonce", "type": "checkbox"}'
```
