# Procédure de gestion des accès

| Référence | Version | Date | Propriétaire | Approbateur | Classification | Statut |
|---|---|---|---|---|---|---|
| NTG-SMSI-PRC-002 | 1.0 | 27/09/2026 | RSSI | RSSI, après avis du CTO et de la responsable RH | Interne | Approuvé |

Exigences couvertes : ISO/IEC 27001:2022, annexe A, mesures 5.11, 5.15 à 5.18, 6.5, 8.2, 8.3 et 8.18. Règles de référence : PSSI, section 5 (ACC-01 à ACC-10) et règle RH-06. Scénarios traités en priorité : R02, R05, R06, R07.

## 1. Objet

Cette procédure décrit le cycle de vie des accès au système d'information de NotAge, de l'arrivée d'une personne à son départ. On parle souvent de cycle **arrivée, mobilité, départ** (en anglais : *joiners, movers, leavers*).

Elle répond directement à la première cause racine des risques de NotAge : des identités et des privilèges non maîtrisés.

## 2. Principes

- **Une personne, une identité.** Chaque personne dispose d'une identité unique, gérée dans l'annuaire Google Workspace et utilisée pour l'authentification unique (SSO). Aucun compte n'est partagé.
- **Moindre privilège et besoin d'en connaître.** Chacun reçoit uniquement les accès nécessaires à sa mission, par un profil prédéfini.
- **Validation à deux niveaux.** Tout accès est demandé par le manager. Il est validé par le propriétaire de l'actif lorsqu'il sort du profil standard.
- **Traçabilité.** Chaque création, modification ou suppression d'accès passe par un ticket, qui en garde la trace.
- **Authentification forte partout.** L'authentification multifacteur est activée dès la création du compte. Les comptes à privilèges utilisent des clés de sécurité physiques.

## 3. Profils d'accès

| Profil | Accès standard | Accès exclus |
|---|---|---|
| Tous les salariés | Google Workspace, Slack, gestionnaire de mots de passe, intranet | Production, données clients |
| Développement | GitHub (dépôts de leur équipe), environnement de recette AWS, outils de suivi | Accès permanent à la production |
| Infrastructure | Comptes AWS de production par élévation temporaire, supervision, coffre de secrets | Aucun accès permanent aux droits étendus, sauf pour les deux administrateurs désignés |
| Support client | Back-office limité aux demandes ouvertes, outil de support | IBAN en clair, export massif |
| Commercial et marketing | CRM, outils marketing | Back-office, données des utilisateurs |
| Finance et RH | Outils de paie, de comptabilité et de gestion RH | Production, données clients |
| Direction | Selon la fonction, accès en lecture aux tableaux de bord | Droits d'administration techniques |

## 4. Arrivée

```mermaid
flowchart LR
    A["J-5 : la RH<br/>ouvre la demande"] --> B["Le manager<br/>choisit le profil"]
    B --> C["L'informatique interne<br/>crée l'identité SSO + MFA"]
    C --> D["J : sensibilisation<br/>et signature de la charte"]
    D --> E["Ouverture des accès<br/>aux données clients"]
```

| Étape | Action | Responsable | Délai |
|---|---|---|---|
| 1 | La RH ouvre la demande d'arrivée : nom, poste, date, manager, type de contrat, date de fin pour les contrats temporaires | Responsable RH | 5 jours ouvrés avant l'arrivée |
| 2 | Le manager choisit le profil d'accès et justifie tout accès supplémentaire | Manager | 3 jours ouvrés avant l'arrivée |
| 3 | L'informatique interne crée l'identité, active l'authentification multifacteur et prépare l'ordinateur géré | Informatique interne | Veille de l'arrivée |
| 4 | Le jour de l'arrivée, la personne signe la charte d'utilisation et l'engagement de confidentialité, puis suit la sensibilisation | RH, RSSI | Jour de l'arrivée |
| 5 | Les accès aux données des clients sont ouverts **seulement après** la sensibilisation | Informatique interne | Après l'étape 4 |

Pour les **stagiaires et prestataires**, le compte porte une date d'expiration égale à la fin du contrat. Un salarié référent est désigné.

## 5. Mobilité

Lors d'un changement de poste ou d'équipe :

1. le nouveau manager demande le profil correspondant au nouveau poste ;
2. les nouveaux accès sont ouverts ;
3. les accès de l'ancien poste qui ne sont plus nécessaires sont **retirés sous 5 jours ouvrés**.

Les droits ne s'additionnent pas au fil des postes : c'est l'une des causes classiques des privilèges excessifs.

## 6. Départ

Le départ est la phase la plus sensible : le scénario R07 (compte d'un ancien salarié resté actif) a déjà été constaté chez NotAge.

| Quand | Action | Responsable |
|---|---|---|
| Dès l'annonce du départ | La RH informe l'informatique interne et la RSSI de la date de fin | Responsable RH |
| Dernier jour, en fin de journée | Désactivation de l'identité SSO, donc de tous les outils raccordés ; révocation des sessions ouvertes et des jetons d'accès | Informatique interne |
| Dernier jour | Désactivation manuelle des outils hors SSO, à partir de la liste tenue à jour | Informatique interne |
| Dernier jour | Restitution de l'ordinateur, des badges et des clés de sécurité ; rappel écrit des obligations de confidentialité | Manager, RH |
| Sous 5 jours ouvrés | Renouvellement des secrets connus de la personne, si elle avait des droits d'administration | Responsable infrastructure |
| Sous 30 jours | Transfert des fichiers utiles au manager, puis suppression du compte | Informatique interne |

> **Départ conflictuel.** En cas de licenciement ou de départ conflictuel, les accès sont désactivés **au moment même** où la décision est notifiée à la personne.

## 7. Comptes à privilèges

- **Administrateurs permanents.** Deux personnes au plus disposent de droits étendus permanents sur AWS : le responsable infrastructure et le CTO. La RSSI n'en fait pas partie, par séparation des tâches.
- **Élévation temporaire.** Les autres membres de l'équipe infrastructure demandent une élévation par ticket, en indiquant le motif. Elle est approuvée par un administrateur permanent autre que le demandeur et limitée à 8 heures. Toutes les élévations sont journalisées et revues chaque mois par la RSSI.
- **Compte d'urgence.** Le compte racine AWS n'est jamais utilisé au quotidien. Il est protégé par une clé de sécurité physique conservée dans un coffre. Toute utilisation déclenche une alerte et ouvre un incident.
- **Outils d'administration.** Les programmes utilitaires à privilèges (consoles d'administration, accès direct aux bases) sont réservés aux administrateurs et journalisés.

## 8. Comptes de service et secrets techniques

- Chaque compte de service a un propriétaire, un usage documenté et les seuls droits nécessaires. Aucune connexion interactive n'est possible avec ce compte.
- Ses secrets sont stockés dans le coffre dédié, jamais dans le code. Ils sont renouvelés au moins une fois par an, et immédiatement en cas d'exposition ou de départ d'une personne qui les connaissait.

## 9. Accès du support aux données des clients

- L'accès au compte d'un client est ouvert automatiquement lorsqu'une demande est ouverte, et fermé à sa clôture.
- Les IBAN sont masqués : seuls les quatre derniers caractères sont visibles.
- Toute consultation est journalisée. Chaque mois, le responsable relation client et la RSSI examinent un échantillon de consultations pour vérifier qu'elles correspondent à une demande.

## 10. Revue trimestrielle des accès

| Étape | Action | Responsable | Délai |
|---|---|---|---|
| 1 | Extraction des comptes et des droits de chaque outil critique : AWS, GitHub, Google Workspace, back-office, outil de support | RSSI | Première semaine du trimestre |
| 2 | Chaque manager et chaque propriétaire d'actif confirme ou retire chaque droit | Managers, propriétaires | 10 jours ouvrés |
| 3 | Retrait des droits non confirmés | Informatique interne, infrastructure | 5 jours ouvrés |
| 4 | Contrôles complémentaires : comptes sans titulaire, comptes inactifs depuis plus de 90 jours (désactivés), comptes à privilèges | RSSI | Pendant la revue |
| 5 | Archivage des extractions et des validations comme preuves de la revue | RSSI | Fin de la revue |

Ces preuves sont des **enregistrements** du SMSI : un auditeur demandera presque toujours à voir la dernière revue des accès.

## 11. Indicateurs

| Indicateur | Cible |
|---|---|
| Comptes désactivés le jour du départ | 100 % |
| Revues trimestrielles réalisées dans les délais | 100 % |
| Comptes sans titulaire détectés lors de la revue | 0 |
| Comptes disposant de droits étendus permanents sur AWS | 2 au plus |
