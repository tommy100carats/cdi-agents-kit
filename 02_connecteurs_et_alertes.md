# Connecteurs et alertes : ce que tu dois faire toi-même

Les agents ne peuvent pas créer de compte ni d'alerte à ta place. Cette partie est **la seule
vraiment manuelle**. Fais-la avant l'installation.

---

## A. Les connecteurs Claude (10 min)

Dans Claude (claude.ai ou l'app), ouvre les **Paramètres**, rubrique **Connecteurs**, et connecte :

| Connecteur | Obligatoire | Pourquoi | Ce qu'il faut autoriser |
|---|---|---|---|
| **Gmail** | Oui | Léa lit tes alertes emploi, Noé lit les réponses des recruteurs, Camille t'envoie le mail du matin | Lecture des mails et envoi de mails |
| **Notion** | Oui | Tout le système vit dans Notion | Accès à ton espace de travail (au minimum à la page parente que l'installation va créer) |
| **Indeed** | Recommandé | Léa cherche directement dans Indeed et lit les annonces en entier | Rien de particulier |
| **Google Drive** | Non | Utile seulement si tu ranges tes CV dans Drive | Lecture |

Vérification : dans une conversation, demande à Claude « Liste mes 3 derniers mails » puis
« Cherche une page dans mon Notion ». S'il y arrive, c'est bon.

> Les tâches planifiées utilisent les mêmes connecteurs. Lors de la création des tâches, si Claude te
> demande d'approuver l'accès, accepte. Si l'option existe, règle chaque tâche sur **approbation
> automatique** : une tâche qui attend ton approbation à 7 h du matin ne tourne pas.

---

## B. Les alertes emploi (20 min)

**Règle d'or : toutes les alertes arrivent sur la même adresse Gmail, celle connectée à Claude.**
Léa les lit chaque matin. Sans alertes, elle n'a que les recherches web, beaucoup moins riches.

Pour chaque site : **une alerte par famille de métier** (pas une seule alerte fourre-tout), fréquence
**quotidienne**, contrat **CDI** ou **temps plein**, ta **zone** (et une alerte « télétravail » à part si tu acceptes le full remote).

### LinkedIn (la plus importante)
1. Va dans **Emplois**, tape l'intitulé principal d'une famille (ex. « Sales Operations »), choisis ta ville.
2. Filtres : **Date de publication : dernières 24 heures**, **Type d'emploi : Temps plein**, niveau d'expérience adapté (ex. Débutant + Confirmé).
3. Active le bouton **Créer une alerte** (ou « Alerte emploi ») en haut des résultats.
4. Dans les paramètres d'alerte : fréquence **quotidienne**, notification **par e-mail**.
5. Recommence pour chaque intitulé important (3 à 8 alertes en tout).

### Welcome to the Jungle
1. Recherche ton intitulé + ta ville, filtre **CDI**.
2. Clique sur **Créer une alerte** et choisis la réception par e-mail.

### Indeed
1. Recherche « intitulé » + « ville », filtre **CDI**.
2. En haut ou en bas des résultats, active **Recevoir les nouvelles offres par e-mail**.

### APEC (si tu es cadre ou bac+4/5)
1. Recherche ton intitulé, filtre **CDI** et ta région.
2. **Créer une alerte**, fréquence quotidienne.

### HelloWork, JobTeaser (jeune diplômé), sites spécialisés de ton métier
Même principe : une recherche propre, puis « créer une alerte ».

### Astuce Gmail (optionnel, recommandé)
Crée un **filtre Gmail** sur les expéditeurs d'alertes avec un libellé « Alertes emploi » et
« Ignorer la boîte de réception ». Ta boîte reste propre, et Léa les trouve quand même (elle cherche dans tout Gmail).

### Note les adresses d'expédition
Quand les premières alertes arrivent, regarde l'adresse de l'expéditeur de chacune et note-la.
L'installation les mettra dans la section 10 des Critères, pour que Léa sache exactement quoi chercher.
Les plus courantes : `jobalerts-noreply@linkedin.com`, `jobs-listings@linkedin.com`, des adresses en
`@welcometothejungle.com`, `@indeed.com`, `@apec.fr`, `@hellowork.com`, `@jobteaser.com`. Elles peuvent changer : fie-toi à ce que tu reçois.

---

## C. Notion (5 min)

1. Crée un compte Notion si tu n'en as pas, dans un **espace personnel dont tu es seul membre**.
2. C'est tout : l'installation crée elle-même les bases. Ne crée rien à la main.
3. Si Notion te demande à quelles pages Claude peut accéder, donne accès à tout l'espace, ou à la
   page « Recherche CDI » une fois qu'elle existe.

---

## D. Tes CV (5 min)

1. Exporte ton ou tes CV en **PDF** (pas une image scannée : du texte sélectionnable).
2. Ajoute-les dans les **fichiers du Projet Claude** « Recherche CDI ».
3. Si tu as plusieurs versions (une orientée « ops », une orientée « commerce »), mets-les toutes : Hugo cherche la meilleure preuve pour chaque exigence d'une annonce, dans n'importe lequel.

---

## E. Niveau avancé, plus tard (optionnel)

**Lire LinkedIn directement.** Les liens LinkedIn des alertes ne s'ouvrent pas depuis le cloud : Léa
retrouve alors l'annonce sur le site de l'entreprise ou sur Indeed, sinon la note est plafonnée (fiche partielle).
Si tu installes l'**app Claude Desktop** et l'extension **Claude in Chrome** sur ton ordinateur, Léa peut
lire LinkedIn dans ton navigateur, en lecture seule, ordinateur allumé. Le bloc correspondant est
prêt en fin de [`agents/01_lea_sourcing.md`](agents/01_lea_sourcing.md). Ne l'active qu'une fois le reste stable.

---

Suivant : [`installation/PROMPT_INSTALLATION.md`](installation/PROMPT_INSTALLATION.md).
