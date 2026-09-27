# Présentation de NotAge

| Référence | Version | Date | Propriétaire | Approbateur | Classification | Statut |
|---|---|---|---|---|---|---|
| NTG-SMSI-CTX-001 | 1.0 | 27/09/2026 | RSSI | Direction générale (CEO) | Interne | Approuvé |

> **Entreprise fictive.** NotAge, ses clients, ses salariés et ses données sont inventés pour les besoins de ce projet. Toute ressemblance avec une entreprise existante serait fortuite.

## 1. Identité

| Élément | Description |
|---|---|
| Raison sociale | NotAge SAS |
| Création | 2019 |
| Siège | Paris (site unique), télétravail de 2 à 3 jours par semaine |
| Effectif | 50 salariés |
| Chiffre d'affaires 2025 | Environ 7 M€, issu d'abonnements |
| Activité | Édition d'une plateforme SaaS de gestion des dépenses professionnelles |
| Clients | Environ 350 entreprises, soit près de 45 000 utilisateurs |
| Hébergement | Amazon Web Services (AWS), région Paris |

## 2. Offre

La plateforme NotAge est accessible sur le web et via une application mobile (iOS et Android). Elle comprend trois modules :

- **Notes de frais** : capture des justificatifs par photo, lecture automatique des montants, calcul des indemnités kilométriques, circuit de validation par les managers et remboursement des salariés.
- **Factures fournisseurs** : réception des factures, rapprochement avec les commandes, circuit de validation et suivi des échéances.
- **Préparation des paiements** : génération des fichiers de virement (format SEPA) pour les remboursements et les factures validées.

Le client valide et transmet lui-même ces fichiers à sa banque : **NotAge ne détient ni ne transfère aucun fonds**.

Des connecteurs (API) permettent d'exporter les écritures vers les logiciels comptables et les ERP des clients.

## 3. Clients et marché

NotAge sert principalement des ETI et des PME françaises. Une dizaine de clients appartiennent au secteur financier (banques, assureurs, sociétés de gestion) et représentent environ 25 % du chiffre d'affaires. Le premier client, une banque régionale, pèse à lui seul 12 % du chiffre d'affaires.

Les données confiées à NotAge sont les suivantes :

- les données personnelles des salariés des clients : identité, coordonnées professionnelles, IBAN personnel pour les remboursements, justificatifs de dépenses révélant déplacements et habitudes ;
- les coordonnées des fournisseurs des clients, dont leurs IBAN ;
- les données financières et comptables des clients.

## 4. Organisation

| Pôle | Effectif | Rôle |
|---|---|---|
| Direction | 3 | CEO, CTO, CFO |
| Technique et produit | 24 | Développement (15), infrastructure et exploitation (3), qualité (2), produit et design (4) |
| Commercial et marketing | 9 | Vente, marketing, avant-vente |
| Relation client et support | 8 | Déploiement, support utilisateurs |
| Fonctions support | 5 | Ressources humaines, finance, services généraux et informatique interne |
| Sécurité | 1 | RSSI, recrutée en juin 2026 et rattachée au CEO |
| **Total** | **50** | |

## 5. Le système d'information en bref

- **Plateforme** : application en conteneurs sur AWS (région Paris), base de données PostgreSQL managée, stockage objet pour les justificatifs, sauvegardes répliquées dans une seconde région de l'Union européenne.
- **Développement** : code source et chaîne d'intégration et de déploiement continus sur GitHub.
- **Outils internes** : Google Workspace (messagerie, documents), Slack, un CRM et un outil de support utilisateurs en SaaS.
- **Postes de travail** : ordinateurs portables fournis par l'entreprise ; smartphones personnels tolérés pour la messagerie et Slack.

La cartographie détaillée et l'inventaire des actifs font l'objet d'un document dédié.

## 6. Situation de départ en sécurité

Constat établi par la RSSI à son arrivée, en juin 2026.

**Points d'appui**

- Chiffrement des données au repos activé sur les services AWS.
- Sauvegardes automatiques de la base de données.
- Revue de code systématique avant toute mise en production.
- Authentification multifacteur sur Google Workspace.
- Disques des ordinateurs portables chiffrés.

**Faiblesses**

- Aucune politique de sécurité formalisée et aucune analyse de risques.
- Droits d'administration AWS étendus accordés à une dizaine de personnes, sans revue périodique.
- Comptes des salariés partis désactivés de façon irrégulière.
- Pas de processus de gestion des incidents ni de surveillance centralisée des journaux.
- Restauration des sauvegardes jamais testée, pas de plan de continuité.
- Fournisseurs jamais évalués sur le plan de la sécurité.
- Aucune action de sensibilisation des salariés.
- Modification des coordonnées bancaires dans la plateforme sans contrôle renforcé.
- Vulnérabilités relevées par un test d'intrusion en 2025 pas toutes corrigées.

## 7. Pourquoi un SMSI maintenant

Trois facteurs motivent le projet :

- **Exigence client.** Au renouvellement de son contrat, la banque cliente exige une certification ISO/IEC 27001 sous 12 mois. Elle impose aussi une annexe contractuelle issue du règlement DORA : notification des incidents, droit d'audit, localisation des données, continuité et réversibilité.
- **Pression commerciale.** Les prospects adressent une quarantaine de questionnaires de sécurité par an, qu'une certification permettrait d'alléger.
- **Croissance.** Une vingtaine de recrutements sont prévus d'ici fin 2027 ; les pratiques informelles ne suffiront plus.

La direction a fixé l'objectif suivant : **audit initial de certification au troisième trimestre 2027**.
