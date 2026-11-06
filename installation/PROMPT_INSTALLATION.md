# Prompt d'installation

**Mode d'emploi.** Ouvre une nouvelle conversation **dans ton Projet Claude « Recherche CDI »**
(celui qui contient tes CV). Sur GitHub, passe la souris sur le bloc gris ci-dessous : un bouton
« copier » (deux petits carrés) apparaît en haut à droite. Clique dessus, colle dans Claude, envoie.
Claude va te poser des questions, puis tout construire. Compte environ 30 minutes.

---

```text
Tu vas installer pour moi « cdi-agents-kit », une chaîne de 5 agents planifiés qui cherche un CDI à ma place : Léa (sourcing), Hugo (notation sur 20), Camille (brief et mail du matin), Noé (suivi Gmail du soir), Revue (calibrage du dimanche). Tout vit dans Notion. Suis les étapes dans l'ordre, montre-moi où tu en es avec une liste de tâches, et demande ma validation aux points marqués VALIDATION. Ne saute aucune étape. N'utilise jamais de tiret long ni de demi-cadratin dans ce que tu écris.

ÉTAPE 0, VÉRIFICATIONS. 
(a) Retrouve les fichiers du kit : ils sont sur le dépôt public https://github.com/tommy100carats/cdi-agents-kit (lis chaque fichier avec WebFetch sur https://raw.githubusercontent.com/tommy100carats/cdi-agents-kit/main/<chemin>). Si je t'ai donné un autre lien de dépôt, utilise-le. S'ils sont dans les fichiers de ce Projet, tu peux aussi les lire là. Il te faut : config/criteres_template.md, config/exemple_rempli.md, notion/schema.json, agents/00_protocole_commun.md à agents/06_ines_cv.md, gabarits/mail_matin.html, calibration/CALIBRATION.md. Lis-les tous en entier avant de continuer.
(b) Vérifie que tu as accès à : Notion (cherche une page), Gmail (cherche mes 3 derniers mails), Indeed (optionnel), et à un outil de tâches planifiées (cherche-le avec ToolSearch si besoin). Si Notion, Gmail ou les tâches planifiées manquent, arrête-toi et dis-moi exactement quoi activer dans les paramètres de Claude.
(c) Liste les CV en PDF présents dans les fichiers du Projet et lis-les. S'il n'y en a aucun, demande-moi d'en ajouter avant de continuer.
(d) Regarde mes 30 derniers jours de Gmail pour repérer les expéditeurs d'alertes emploi (LinkedIn, Welcome to the Jungle, Indeed, APEC, HelloWork, JobTeaser, autres). Note les adresses exactes. S'il n'y en a aucune, dis-moi que mes alertes ne sont pas encore en place (voir 02_connecteurs_et_alertes.md) : on peut continuer, mais Léa sera moins efficace.

ÉTAPE 1, QUESTIONNAIRE. Pose-moi les questions du questionnaire (01_questionnaire.md, résumé ci-dessous) PAR BLOCS, pas toutes d'un coup, en utilisant des questions à choix quand c'est possible. Si je t'ai déjà donné mes réponses, ne repose que ce qui manque. Pour chaque question, propose une valeur par défaut raisonnable tirée de mes CV.
- Bloc 1, métier : familles visées par priorité (2 à 5), intitulés FR et EN de chacune, mots-clés de recherche, condition éventuelle par famille, intitulés à écarter, chasse pure exclue ou non.
- Bloc 2, niveau : années d'expérience totales et dans le métier, nombre d'années maximum demandé dans une annonce, mots du titre qui veulent dire trop senior.
- Bloc 3, contrat et lieu : contrats acceptés, commune de référence, trajet idéal et maximum, zones acceptées et écartées, télétravail minimum, full remote France, full remote étranger.
- Bloc 4, salaire : plancher et cible en k€ brut annuel fixe.
- Bloc 5, entreprises : types préférés et leur définition vérifiable, taille minimum, secteurs aimés et évités, liste d'entreprises de rêve (avec page carrières si connue), entreprises à ne jamais proposer.
- Bloc 6, profil : à partir de mes CV, PROPOSE-MOI la section 4 (résumé, expériences avec réalisations chiffrées, outils avec niveau, langues, diplômes) et je corrige. Puis demande-moi la liste des interdits : ce que le système ne doit jamais affirmer sur moi.
- Bloc 7, fonctionnement : mon adresse Gmail (seule destinataire autorisée), max d'offres dans le mail, seuils, ancienneté max d'une offre, jours de sourcing, ce qui me fait dire oui à coup sûr, ce qui me fait dire non à coup sûr.
Règle : tu n'inventes rien sur moi. Ce que je ne sais pas prend la valeur par défaut du template, et tu me le dis.

ÉTAPE 2, PAGE CRITÈRES. Remplis config/criteres_template.md avec mes réponses (Mode = calibration). Pour les entreprises de la section 8, cherche toi-même leur page carrières et leur ATS (Ashby, Greenhouse, Lever, Teamtailor, Welcome to the Jungle) avec WebSearch, et indique le slug quand tu le trouves ; si tu ne le trouves pas, écris « site carrières » et le lien. Mets en section 10 les expéditeurs d'alertes trouvés à l'étape 0 (d). VALIDATION : montre-moi la page complète et attends mon accord avant d'écrire dans Notion.

ÉTAPE 3, NOTION. Avec le connecteur Notion, crée exactement la structure de notion/schema.json, sans renommer aucune propriété :
(a) la page parente « Recherche CDI » dans mon espace (à la racine de mon espace privé, ou là où je te le dis) ;
(b) sous elle, la page « Critères et entreprises cibles » avec le contenu validé à l'étape 2 ;
(c) les bases « Journal d'analyse », « Offres », « Runs » avec toutes leurs propriétés et options (pour la propriété Famille, les options sont mes familles plus « Autre ») ; puis leurs vues si l'outil le permet (sinon, liste-moi les vues à créer à la main en 2 minutes) ;
(d) les pages « Registre de calibrage » (avec R1, R2 et mes règles oui/non en R3 et R4) et « Entonnoir » (tableau à zéro).
Récupère et note : l'id de la page parente, de la page Critères, du Registre, de l'Entonnoir ; l'id de data source (collection://...) du Journal, d'Offres et de Runs ; les URL de la base Offres, du Journal et de la page Entonnoir. Écris-les dans la section « Identifiants » de la page Critères. Puis fais un test d'écriture : crée une ligne dans Runs (Run = « Installation AAAA-MM-JJ HH:MM », Agent = Installation, Statut run = OK, Résumé = « installation du kit »). Si une écriture échoue, corrige avant de continuer.

ÉTAPE 4, ASSEMBLAGE DES PROMPTS. Pour chacun des 5 agents planifiés (Léa, Hugo, Camille, Noé, Revue), assemble le prompt complet = agents/00_protocole_commun.md suivi du fichier de l'agent, sans les commentaires HTML <!-- -->. Remplace UNIQUEMENT ces marqueurs d'installation par les vraies valeurs : {{PRENOM}}, {{NOM}}, {{EMAIL}}, {{ID_PARENT}}, {{ID_CRITERES}}, {{DS_JOURNAL}}, {{DS_OFFRES}}, {{DS_RUNS}}, {{ID_REGISTRE}}, {{ID_ENTONNOIR}}, {{URL_OFFRES}}, {{URL_JOURNAL}}, {{URL_ENTONNOIR}}, {{DATE_INSTALLATION}}. Pour Camille, remplace {{GABARIT_MAIL}} par le contenu complet de gabarits/mail_matin.html, dans lequel tu remplaces aussi {{PRENOM}}, {{URL_OFFRES}}, {{URL_JOURNAL}}, {{URL_ENTONNOIR}} ; les autres marqueurs du gabarit ({{SCORE}}, {{POSTE}}, {{FIT}}, etc.) restent tels quels, Camille les remplit chaque matin. Vérifie qu'il ne reste aucun marqueur d'installation non remplacé. Assemble aussi le prompt d'Inès (06_ines_cv.md, protocole commun non nécessaire).
Sauvegarde : écris les 6 prompts assemblés dans le Projet (project_write, claude/prompts/<agent>.md) et dans une page Notion « Prompts des agents (sauvegarde) » sous la page parente.

ÉTAPE 5, TÂCHES PLANIFIÉES. VALIDATION : montre-moi le tableau ci-dessous avec les horaires, et demande-moi si je veux les changer. Puis crée les 5 tâches planifiées, chacune avec son prompt assemblé, en heure de Paris :
| Nom | Horaire | Cron |
| Léa, sourcing | 07:15 du lundi au samedi | CRON_TZ=Europe/Paris 15 7 * * 1-6 |
| Hugo, notation | 08:15 du lundi au samedi | CRON_TZ=Europe/Paris 15 8 * * 1-6 |
| Camille, brief et mail | 09:05 du lundi au samedi | CRON_TZ=Europe/Paris 5 9 * * 1-6 |
| Noé, suivi du soir | 19:10 tous les jours | CRON_TZ=Europe/Paris 10 19 * * * |
| Revue du dimanche | 18:10 le dimanche | CRON_TZ=Europe/Paris 10 18 * * 0 |
Les 4 heures d'écart entre Léa et Camille sont voulues : chaque agent doit avoir fini avant que le suivant commence. Si mes jours de sourcing diffèrent, adapte les crons de Léa, Hugo et Camille. Les tâches tournent dans le cloud, sans mon ordinateur. Après création, dis-moi pour chacune si elle est en approbation automatique ; sinon explique-moi où activer « Approuver automatiquement » dans ses réglages, sinon les runs attendront mon accord et ne tourneront pas.

ÉTAPE 6, PREMIER TEST. Lance Léa maintenant (déclenche la tâche si l'outil le permet, sinon exécute son prompt ici même). Quand elle a fini, lance Hugo. Puis montre-moi : la ligne Runs de chacun, le nombre d'offres analysées, transmises et notées, et les 5 meilleures notes avec le détail. Si quelque chose a échoué, explique la cause et corrige (voir docs/depannage.md) avant de conclure.

ÉTAPE 7, CONCLUSION. Résume en 10 lignes : ce qui est créé (avec les liens Notion), les horaires, le mode actuel (calibration), et la suite : la semaine de calibration décrite dans calibration/CALIBRATION.md, puis le passage en production en changeant Mode dans la page Critères. Rappelle-moi les trois choses que je fais chaque jour : lire le mail du matin, passer les offres choisies en « Je postule » puis « Postulé » dans Offres, lire le point du soir s'il arrive.
```

---

## Si l'installation s'arrête en route

Recolle simplement le prompt dans une nouvelle conversation du Projet en ajoutant en tête :
« Reprise : l'installation s'est arrêtée à l'étape N. Vérifie ce qui existe déjà dans Notion
(page Recherche CDI) avant de recréer quoi que ce soit, et ne crée jamais de doublon. »
