# immo-ops-mvp — STATUS (29/01/2026)

## Objectif
MVP “Immo Ops” vendable : rendre les outils de l’agence intelligents sans changer de CRM.
Cible : agences immobilières. Output : relances + suivi mandat + génération d’annonce.

## État actuel (OK)
### W3 — Fin de mandat J-15 (Airtable)
- Trigger : schedule quotidien 08:00
- Find records : mandats avec “Date J-15 = today” + “Alerte fin mandat envoyée le” vide
- Action : email à l’agent (champ Email agent texte / flatten value)
- Anti-spam : update “Alerte fin mandat envoyée le = now”
✅ Fonctionnel

### W4 — Documents manquants (Airtable)
- Trigger : checkbox “Déclencheur relance docs”
- Condition : “Docs manquants” non vide
- Action : email au vendeur (champ Email vendeur)
- Anti-spam : update “Relance docs envoyée le = now” (+ option décocher trigger)
✅ Fonctionnel

## À faire ensuite (priorité)
### W1 — Génération d’annonce IA (Cloud)
But : 1 clic dans Airtable → annonce générée et stockée dans “Annonce IA”.
Stack : Airtable (données) + n8n Cloud (orchestration) + LLM (génération) + GitHub (versioning prompts).

Champs à ajouter dans table “Biens” (Airtable)
- Générer annonce (checkbox)
- Annonce IA (long text)
- Annonce générée le (date/time)
- Brief annonce (long text)
- Prompt version (single line)
- Erreur annonce (long text)

Connexion n8n ↔ Airtable
- Créer un Airtable PAT (read/write records, base limitée)
- Ajouter credential Airtable dans n8n Cloud
- Workflow n8n : Cron → List (Générer annonce checked & Annonce générée le empty) → LLM → Update record

### W2 — Bien dormant 21j (Airtable)
But : détecter les biens sans activité depuis X jours et relancer l’agent.
À faire après W1.

## Démo (script 3–5 min)
1) Promesse : “On rend vos outils intelligents sans changer de CRM.”
2) W3 : mandat à J-15 → email agent
3) W4 : docs manquants → email vendeur
4) W1 : (bientôt) checkbox “Générer annonce” → annonce IA remplie
5) Close : installation rapide + packs

## Rôles (qui fait quoi)
- Oli : pilotage + Airtable + démo + arbitrage produit
- Maxime : terrain, feedback agences, vente / RDV
- Mohamed (si onboarding) : industrialisation phase 2 (n8n robuste, OCR, intégrations CRM)

## Liens
- Repo GitHub : https://github.com/ProNeXus-AIAA/immo-ops-mvp
- Base Airtable : (à coller ici)
- n8n Cloud : (à coller ici)