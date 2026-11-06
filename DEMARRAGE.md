# Démarrage : de zéro à ton premier mail du matin

Compte une demi-journée la première fois, puis 15 minutes par jour pendant la semaine de calibration.
Coche au fur et à mesure.

## Ce qu'il te faut

- [ ] Un compte **Claude** avec un abonnement payant qui donne accès aux **connecteurs** et aux **tâches planifiées** (vérifie dans claude.ai, rubrique Paramètres, que tu peux connecter Gmail et Notion et créer une tâche planifiée).
- [ ] Une adresse **Gmail** (c'est elle qui reçoit les alertes emploi et les réponses des recruteurs).
- [ ] Un compte **Notion** gratuit, dans un espace de travail personnel dont tu es seul membre.
- [ ] Un compte **LinkedIn**, et idéalement **Welcome to the Jungle**, **Indeed**, **APEC** (si tu es cadre), **HelloWork**.
- [ ] **Ton CV en PDF**. Idéalement 2 à 4 versions (une par type de poste visé) : plus Hugo a de preuves, plus ses notes sont justes.

## Étape 1. Répondre au questionnaire (20 min)

Ouvre [`01_questionnaire.md`](01_questionnaire.md) et prépare tes réponses dans un fichier texte.
Tu peux aussi sauter cette étape : le prompt d'installation te posera les questions une par une.
Mais réfléchir avant donne de bien meilleurs résultats, surtout sur les **métiers visés** et les **exclusions**.

## Étape 2. Créer tes alertes emploi (20 min)

Suis la partie B de [`02_connecteurs_et_alertes.md`](02_connecteurs_et_alertes.md).
Toutes les alertes doivent arriver **sur la même adresse Gmail**. C'est la source principale de Léa.

- [ ] Alertes LinkedIn (une par métier visé, quotidiennes)
- [ ] Alertes Welcome to the Jungle
- [ ] Alertes Indeed
- [ ] Alertes APEC et HelloWork (selon ton profil)

## Étape 3. Brancher les connecteurs dans Claude (10 min)

Suis la partie A de [`02_connecteurs_et_alertes.md`](02_connecteurs_et_alertes.md).

- [ ] Gmail connecté
- [ ] Notion connecté (avec accès à ton espace)
- [ ] Indeed connecté (s'il est proposé dans le répertoire des connecteurs)

## Étape 4. Créer le Projet Claude (5 min)

- [ ] Dans Claude, crée un **Projet** nommé « Recherche CDI ».
- [ ] Dans les fichiers du projet, ajoute **tes CV en PDF**. Nomme-les clairement, par exemple `CV_Prenom_Nom_SalesOps.pdf`.
- [ ] Rien d'autre à télécharger : le prompt d'installation donne à Claude le lien du kit, et il lit lui-même les fichiers sur GitHub. Pas besoin de compte GitHub.

## Étape 5. Lancer l'installation (30 min, Claude fait le travail)

- [ ] Ouvre une **nouvelle conversation dans le Projet**.
- [ ] Copie-colle tout le contenu de [`installation/PROMPT_INSTALLATION.md`](installation/PROMPT_INSTALLATION.md).
- [ ] Réponds à ses questions (ou colle tes réponses du questionnaire).
- [ ] Valide ce qu'il te propose à chaque étape. Il va :
  1. écrire ta page « Critères » dans Notion,
  2. créer les 3 bases Notion et les 2 pages de suivi,
  3. préparer les 5 agents avec tes identifiants,
  4. créer les 5 tâches planifiées,
  5. lancer un premier test de Léa et Hugo.

## Étape 6. Semaine de calibration (15 min par jour)

Suis [`calibration/CALIBRATION.md`](calibration/CALIBRATION.md).
Le système démarre en **mode calibration** : il note mais n'envoie pas encore de mail.
Tu notes toi-même 20 offres, tu compares à Hugo, et tu corriges. Après ça, tu passes en **production**.

## Étape 7. La routine, une fois en production

| Quand | Toi | Le système |
|---|---|---|
| Le matin | Tu lis le mail de Camille, tu ouvres les offres, tu passes celles qui t'intéressent en « Je postule » dans Notion | Léa, Hugo, Camille ont tourné |
| Quand tu postules | Tu passes la fiche en « Postulé » dans Notion | Noé lance le suivi |
| Le soir | Tu lis le point de Noé s'il y en a un (il ne t'écrit que s'il y a quelque chose) | Noé lit Gmail et met à jour |
| Le dimanche | Tu lis le bilan, tu réponds « Valide R4 » ou « Refuse R4 » aux règles proposées | La Revue mesure et propose |

## Si quelque chose ne marche pas

Regarde [`docs/depannage.md`](docs/depannage.md). Le réflexe : ouvrir la base **Runs** dans Notion.
Chaque agent y écrit une ligne à chaque passage, même quand il échoue, avec ce qu'il a lu, écrit, et ce qui a coincé.
