# Ton Notion : ce qu'il contient et comment t'en servir

L'installation crée tout. Cette page t'explique quoi regarder, et surtout **quoi toucher et quoi ne pas toucher**.

```
Recherche CDI
├── 🧭 Critères et entreprises cibles   ← TA page : tu la modifies quand ta recherche évolue
├── ⭐ Offres                            ← TA base : tu décides ici
├── 📥 Journal d'analyse                 ← tout ce que Léa a vu (lecture, et calibration)
├── 📊 Entonnoir                         ← tes chiffres, mis à jour chaque soir
├── 📏 Registre de calibrage             ← les règles apprises (tu valides ou refuses)
├── 🧾 Runs                              ← le carnet de bord des agents (en cas de souci)
└── Prompts des agents (sauvegarde)
```

## Ce que tu touches

| Où | Quoi | Quand |
|---|---|---|
| **Offres** › Ma décision | « Je postule » quand une offre te plaît, « Postulé » quand c'est fait, « Pas pour moi » sinon | Chaque matin |
| **Offres** › Mon commentaire | Une phrase quand tu refuses une offre bien notée | Quand ça arrive |
| **Journal** › Mon score, Mon avis | Ta note pendant la calibration | Semaine 1 |
| **Registre** › Statut | Validée ou Refusée pour chaque règle proposée | Le dimanche |
| **Critères** | Tout : métiers, salaire, lieu, entreprises, mode | Quand ta recherche change |

## Ce que tu ne touches pas

- Les **noms des propriétés** des bases (les agents les utilisent tels quels : renommer « Score /20 » casse Hugo).
- Les colonnes **Run Léa, Run Hugo, Run Camille**, **Étape**, **Résultat** (ce sont les traces des agents).
- La section **Identifiants** de la page Critères.

Tu peux sans risque : ajouter des vues, des filtres, des propriétés à toi (par exemple « Contact interne »), réordonner les colonnes.

## Le cycle d'une offre

```
Léa la trouve ─→ Journal (À noter) ─→ Hugo la note
                                         ├─ moins de 12 : Non retenue (reste dans le Journal, avec la raison)
                                         ├─ 12 à 13 : En veille (réserve)
                                         └─ 14 et plus : À briefer ─→ Camille : fiche dans Offres + mail
                                                                         └─→ Toi : Je postule ─→ Postulé
                                                                                 └─→ Noé : Accusé, Entretien, Offre reçue ou Refus
```

## Changer de cible en cours de route

Exemple : tu ajoutes le métier « Chef de projet ». Ouvre la page Critères :
1. section 1 : ajoute une ligne (priorité, famille, intitulés, mots-clés),
2. ajoute l'option « Chef de projet » à la propriété Famille du Journal et d'Offres,
3. crée une alerte LinkedIn et Welcome to the Jungle sur cet intitulé.
C'est tout : dès le lendemain, Léa et Hugo en tiennent compte. Les prompts ne changent pas.

## Mettre en pause (vacances, offre acceptée)

Section 0 de la page Critères : `Mode = pause`. Les agents tournent, voient la pause, écrivent
« Rien à faire » et s'arrêtent. Repasse en `production` pour reprendre.
