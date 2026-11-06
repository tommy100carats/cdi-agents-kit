# Critères et entreprises cibles

> Cette page est le **référentiel unique** de la chaîne d'agents. Tous les agents la lisent au début
> de chaque run. Pour changer de cible, modifie cette page, jamais les prompts.
> Les valeurs entre `{{ }}` sont remplies à l'installation. Version du contenu : 1, du {{DATE_INSTALLATION}}.

## 0. Paramètres

| Paramètre | Valeur | Rôle |
|---|---|---|
| Mode | calibration | `pause` : personne n'écrit. `calibration` : Hugo note, aucun mail, rien n'est envoyé. `production` : chaîne complète |
| Candidat | {{PRENOM}} {{NOM}} | Pour les mails et les briefs |
| Email du candidat | {{EMAIL}} | Seul destinataire autorisé de tout mail |
| Fuseau horaire | Europe/Paris | Horodatages |
| Seuil top | {{SEUIL_TOP, défaut 14}} | Note minimum pour le mail du matin |
| Seuil veille | {{SEUIL_VEILLE, défaut 12}} | De ce seuil au seuil top : réserve |
| Max offres dans le mail | {{MAX_MAIL, défaut 5}} | |
| Max par entreprise dans le mail | 2 | |
| Fenêtre de publication | {{FENETRE, défaut 10}} jours | Au-delà, l'offre est écartée |
| Plafond transmis à Hugo par run | 15 | Le surplus va en veille |
| Objectif offres analysées par jour | 30 | Si Léa est en dessous, elle élargit ses requêtes |
| Fenêtre Gmail de Noé | 4 jours | |
| Délai de relance après candidature | 10 jours | |
| Silence avant « Sans réponse » | 21 jours | |
| Budget Léa | 30 minutes | Les autres agents : 20 minutes |

## 1. Métiers ciblés

| Priorité | Famille | Intitulés qui entrent (FR et EN) | Mots-clés de recherche | Condition |
|---|---|---|---|---|
| 1 | {{FAMILLE_1}} | {{INTITULES_1}} | {{MOTS_CLES_1}} | {{CONDITION_1, ou « aucune »}} |
| 2 | {{FAMILLE_2}} | {{INTITULES_2}} | {{MOTS_CLES_2}} | {{CONDITION_2}} |
| 3 | {{FAMILLE_3, optionnel}} | | | |

Points de la grille (critère B) : priorité 1 = 4, priorité 2 = 3, priorité 3 = 2, poste mixte (une famille visée avec une part minoritaire de ce qui est exclu) = 1, autre = 0.
Une famille avec une condition non remplie n'est pas notée : l'offre est écartée avec la raison « Entreprise hors périmètre » ou « Condition non remplie ».

## 2. Exclusions fermes (appliquées par Léa, dans cet ordre)

1. Contrats exclus : {{CONTRATS_EXCLUS, défaut : stage, alternance, CDD, intérim, freelance, VIE}} → « Pas un CDI ».
2. Intitulés exclus : {{INTITULES_EXCLUS}} → « Intitulé exclu ».
3. Chasse ou prospection pure (si exclue) : {{CHASSE_EXCLUE, ex. SDR, BDR, Business Developer new business, Account Executive hunter}} → « Chasse / new business ».
4. Séniorité : mots du titre {{MOTS_SENIOR, défaut : Senior, Lead, Head, Director, VP}} → « Trop senior ». Plus de {{ANNEES_MAX}} ans écrits dans l'annonce → « Plus de {{ANNEES_MAX}} ans demandés ».
5. Métiers hors périmètre : {{METIERS_HORS, ex. ingénieur, produit, data, finance pure}} → « Métier hors périmètre ».
6. Type ou taille d'entreprise : voir section 3 → « Entreprise hors périmètre ».
7. Lieu : voir section 6 → « Lieu hors périmètre ».
8. Publiée depuis plus que la fenêtre (section 0) → « Publiée il y a trop longtemps ». Date introuvable : l'offre passe avec « date inconnue ».
9. Offre fermée, page 404 → « Offre fermée » ou « Page introuvable ».
10. Clé déjà vue → « Doublon ».

## 3. Types d'entreprise

| Type | Définition (vérifiable, sourcée) | Points D | Familles éligibles |
|---|---|---|---|
| {{TYPE_1, ex. Startup ayant levé}} | {{ex. levée datée dans les 24 derniers mois}} | 3 | {{toutes / priorité 1 seulement...}} |
| {{TYPE_2, ex. Scale-up}} | {{ex. série B ou plus, ou 200 salariés et plus en croissance}} | 3 | |
| {{TYPE_3, ex. Grand groupe}} | {{ex. 1 000 salariés et plus ou filiale d'un groupe coté, tous secteurs}} | 3 | |
| {{TYPE_4, ex. PME ou ETI}} | | {{1 ou 2}} | |
| Non identifiable | Aucune source trouvée en deux recherches | 0 | aucune famille sous condition |

Taille minimum : {{TAILLE_MIN, ex. 50}} salariés.
Secteurs appréciés (bonus via le registre si tu le souhaites) : {{SECTEURS_PLUS}}.
Secteurs à éviter (écartés par Léa) : {{SECTEURS_MOINS}}.

## 4. Profil du candidat (seule source de preuves avec les CV)

**Résumé.** {{2 lignes : années d'expérience totales, dans le métier visé, positionnement}}

**Expériences** (du plus récent au plus ancien)
- {{Entreprise}}, {{poste}}, {{dates}} : {{réalisation chiffrée 1}} ; {{réalisation 2}} ; {{réalisation 3}}
- ...

**Outils** : {{outil (niveau)}}, ...
**Langues** : {{langue (niveau réel)}}
**Diplômes et certifications** : {{...}}

**Interdits** (le système ne l'affirme jamais, même si une annonce le demande)
- {{ex. jamais « expert Salesforce » : notions seulement}}
- Aucun chiffre qui n'est ni dans cette section ni dans les CV.

Fichiers CV dans le Projet Claude : {{LISTE_DES_NOMS_DE_FICHIERS_CV}}

## 5. Grille de notation de Hugo (sur 20, additive, sans malus)

| Critère | Points | Règle |
|---|---|---|
| A. Couverture des exigences | 0 à 8 | Chaque exigence de l'annonce : preuve verbatim couverte 1, partielle 0,5, absente 0. A = somme / nombre × 8, arrondi à l'inférieur. Fiche partielle : A plafonné à 5 |
| B. Nature du poste | 0 à 4 | Selon la priorité de la famille (section 1) |
| C. Niveau | 0 à 3 | 0 à {{ANNEES_CONFORT, ex. 3}} ans demandés = 3 ; jusqu'à {{ANNEES_MAX}} ans = 2 ; non précisé = 1 |
| D. Entreprise | 0 à 3 | Selon le type (section 3) |
| E. Conditions | 0 à 2 | Lieu et télétravail compatibles (section 6) = 1 ; salaire absent ou au moins au plancher (section 7) = 1 |
| Ajustement registre | au plus 2 | Règles validées du Registre de calibrage, citées par numéro |

Verdict : dossier déjà ouvert chez l'employeur → « Dossier déjà ouvert » ; fiche partielle et note ≥ seuil veille → « Plafonnée fiche partielle » ; note ≥ seuil top → « Top » ; note ≥ seuil veille → « Veille » ; sinon « Non retenue ». En cas d'hésitation, la note basse.

## 6. Lieu et télétravail

- Commune de référence pour les trajets : {{COMMUNE_REF}}
- Trajet idéal : {{TRAJET_IDEAL}} min. Accepté si l'offre est très bonne : {{TRAJET_MAX}} min.
- Zones acceptées : {{ZONES_OK, ex. Paris et petite couronne}}
- Zones écartées d'office : {{ZONES_KO}}
- Télétravail minimum : {{TELETRAVAIL_MIN}}
- Full remote France : {{oui / non}}. Full remote étranger (Europe, EMEA) : {{oui / non}}.

## 7. Salaire

- Plancher : {{PLANCHER}} k€ brut annuel fixe. Cible : {{CIBLE}} k€.
- Salaire non affiché : jamais pénalisé, jamais estimé.

## 8. Entreprises cibles (Léa visite leurs pages carrières)

| Entreprise | Type (section 3) | Page carrières ou ATS | Note |
|---|---|---|---|
| {{...}} | | {{ex. Ashby : slug « alan » ; Lever : slug « qonto » ; Greenhouse : slug « datadog » ; Teamtailor ; WTTJ ; site}} | |

## 9. Entreprises exclues

{{Liste, avec la raison. Léa écarte, Hugo ne note pas.}}

## 10. Sources

**Expéditeurs d'alertes dans Gmail** (Léa les cherche chaque matin) :
{{ex. jobalerts-noreply@linkedin.com, jobs-listings@linkedin.com, welcometothejungle.com, indeed.com, apec.fr, hellowork.com}}

**Recherches Indeed** : chaque mot-clé de la section 1, sur {{ZONE_RECHERCHE}}, puis « remote France » si accepté.

**Recherches web** : au plus 8 par run, sur les mots-clés de la section 1, en variant les sites (welcometothejungle.com, jobs.lever.co, jobs.ashbyhq.com, boards.greenhouse.io, apec.fr).

## Identifiants (remplis à l'installation, ne pas modifier)

| Objet | Identifiant |
|---|---|
| Page parente « Recherche CDI » | {{ID_PARENT}} |
| Cette page Critères | {{ID_CRITERES}} |
| Journal d'analyse (data source) | {{DS_JOURNAL}} |
| Offres (data source) | {{DS_OFFRES}} |
| Runs (data source) | {{DS_RUNS}} |
| Registre de calibrage (page) | {{ID_REGISTRE}} |
| Entonnoir (page) | {{ID_ENTONNOIR}} |
| URL de la base Offres | {{URL_OFFRES}} |
| URL du Journal | {{URL_JOURNAL}} |
| URL de l'Entonnoir | {{URL_ENTONNOIR}} |
