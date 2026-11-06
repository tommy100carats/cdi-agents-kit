# Dépannage

**Premier réflexe : ouvre la base Runs dans Notion.** Chaque agent y écrit une ligne à chaque passage,
même en échec, avec un Statut (OK, Partiel, Échec, Rien à faire), ce qu'il a lu et écrit, et une colonne « À signaler ».
Pas de ligne du tout = l'agent n'a pas tourné.

| Symptôme | Cause probable | Solution |
|---|---|---|
| Aucune ligne Runs pour un agent | La tâche attend une approbation, ou elle est désactivée | Ouvre les réglages de la tâche planifiée, active l'approbation automatique si ton organisation le permet, vérifie qu'elle est active. Ou réponds à la demande d'approbation en attente |
| Pas de mail du matin | Mode = calibration ; ou aucune offre à 14 et plus ; ou Camille a tourné avant la fin de Hugo | Regarde la ligne Runs de Camille : « Rien à faire » = aucune offre Top. Vérifie le Mode. Espace les horaires |
| Le mail arrive dans les spams ou Promotions | Mail envoyé depuis ta propre adresse vers toi-même, filtré | Crée un filtre Gmail sur l'objet « offres qui te ressemblent » : « Ne jamais envoyer dans le spam », « Marquer comme important » |
| Léa analyse moins de 10 offres | Alertes absentes, trop étroites, ou mal reconnues | Vérifie la section 10 des Critères (adresses d'expéditeurs exactes), ajoute des alertes, des mots-clés en anglais, des entreprises cibles avec ATS en section 8 |
| Beaucoup de « Fiche lue = Partielle » | Liens LinkedIn non lisibles depuis le cloud | Normal en partie. Ajoute des alertes Welcome to the Jungle et Indeed, des entreprises en section 8, ou active le niveau avancé LinkedIn (fin de agents/01_lea_sourcing.md) |
| Run « Partiel » avec « quota SQL » | Le connecteur Notion limite les requêtes SQL rapprochées | Rien à faire, les agents basculent en mode rows. Si ça se répète, décale l'agent de 10 minutes |
| Run « Partiel » « budget dépassé » | Trop de sources pour le temps imparti | Réduis le nombre d'entreprises en section 8 ou monte le budget de Léa (section 0) |
| Welcome to the Jungle « 429 » | Limitation de débit du site | Normal, Léa s'arrête volontairement à 3 lectures. Les alertes mail WTTJ restent lues |
| Des lignes restent « À noter » plusieurs jours | Hugo n'a pas tourné, ou a échoué | Runs de Hugo. Il reprend toujours toutes les lignes en attente, rien n'est perdu |
| Hugo note à côté | Critères imprécis ou preuves absentes des CV | Voir le tableau de calibration/CALIBRATION.md |
| Un statut de candidature ne bouge pas | Le mail du recruteur ne contient pas le nom de l'entreprise, ou vient d'un ATS inconnu | Noé le met dans « À valider ». Sinon, mets le statut à jour à la main : Noé ne revient jamais en arrière |
| Noé propose une fiche à valider | Tu as postulé en dehors du système | Crée la fiche dans Offres (ou dis-le à Claude), Noé la suivra |
| Une offre fermée est dans le mail | L'annonce a été retirée entre le sourcing et l'envoi | Passe la fiche en « Pas pour moi » avec le commentaire « fermée » |
| Notion signale une limite de blocs | Espace partagé avec d'autres membres sur un plan gratuit | Utilise un espace personnel dont tu es seul membre |
| Un agent a fait quelque chose d'interdit | Prompt modifié, ou instruction lue dans une annonce | Vérifie que le prompt de la tâche est identique à la sauvegarde (page « Prompts des agents (sauvegarde) »). Signale-le dans une conversation Claude en collant la ligne Runs |

## Modifier un agent

1. Ne modifie un prompt que si la page Critères ne suffit pas (c'est rare).
2. Fais-le dans une conversation du Projet : « Mets à jour la tâche planifiée Hugo : <changement>. Montre-moi le diff avant d'appliquer. Ne supprime ni ne recrée la tâche. »
3. Mets à jour la sauvegarde dans Notion et dans le Projet.

## Repartir de zéro

Ne supprime rien : passe le Mode à `pause`, puis relance le prompt d'installation avec « Reprise ».
Les anciennes lignes servent d'historique et de dédoublonnage.
