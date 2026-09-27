# Maîtrise des informations documentées

| Référence | Version | Date | Propriétaire | Approbateur | Classification | Statut |
|---|---|---|---|---|---|---|
| NTG-SMSI-DOC-001 | 1.0 | 27/09/2026 | RSSI | Direction générale (CEO) | Interne | Approuvé |

Exigence couverte : ISO/IEC 27001:2022, article 7.5.

## 1. Objet

Ce document fixe la façon dont NotAge crée, approuve, diffuse, protège et conserve les informations documentées de son SMSI. Il tient aussi le registre de ces documents.

On distingue deux familles d'informations documentées :

- **Les documents** disent ce qu'il faut faire : politiques, procédures, méthodes. Ils évoluent par versions successives.
- **Les enregistrements** prouvent ce qui a été fait : registre des risques, comptes rendus, rapports d'audit, journaux. Ils ne se modifient pas après coup.

## 2. Identification

Chaque document porte un en-tête qui contient :

- une référence unique au format `NTG-SMSI-<type>-<numéro>` ;
- sa version, sa date, son propriétaire et son approbateur ;
- sa classification et son statut.

| Code | Type de document |
|---|---|
| DOC | Maîtrise documentaire |
| CTX | Contexte et périmètre |
| POL | Politiques |
| GOV | Organisation et gouvernance |
| RSK | Risques |
| DDA | Déclaration d'applicabilité |
| PSSI | Politique de sécurité des systèmes d'information |
| PRC | Procédures |
| PIL | Pilotage et mesure |
| AUD | Audit et amélioration |

## 3. Versions et approbation

- **Numérotation** : les brouillons portent une version 0.x. La version 1.0 correspond à la première approbation. Une modification mineure (forme, correction) incrémente le chiffre après le point. Une modification de fond incrémente le premier chiffre et exige une nouvelle approbation.
- **Approbation** :

  | Documents | Approuvés par |
  |---|---|
  | Politiques, PSSI, périmètre, déclaration d'applicabilité | Direction générale |
  | Procédures et méthodes | RSSI, après avis du responsable de l'activité concernée |
  | Enregistrements | Validés par leur propriétaire |

- **Revue** : tout document est revu au moins une fois par an, et à chaque changement significatif de l'organisation, du système d'information ou des risques.
- **Obsolescence** : une version remplacée est archivée et marquée « Obsolète ». Seule la version approuvée en vigueur est diffusée.

## 4. Classification de l'information

| Niveau | Définition | Exemples |
|---|---|---|
| Public | Diffusion libre sans préjudice | Site web, plaquettes commerciales |
| Interne | Réservé aux salariés et prestataires sous contrat | Politiques et procédures du SMSI |
| Confidentiel | Réservé aux personnes qui en ont besoin ; une divulgation porterait préjudice à NotAge ou à ses clients | Registre des risques, contrats, données clients |
| Strictement confidentiel | Accès nominatif et limité ; une divulgation aurait des conséquences graves | Secrets d'authentification, clés de chiffrement, résultats de tests d'intrusion |

Les règles de manipulation associées à chaque niveau sont précisées dans la PSSI.

## 5. Stockage, diffusion et conservation

- **Stockage.** Les documents du SMSI sont centralisés dans un espace partagé dédié. Les documents « Interne » y sont consultables par tous les salariés. La modification est réservée aux propriétaires. L'accès aux documents « Confidentiel » est nominatif.
- **Documents d'origine externe.** Normes, textes réglementaires et contrats clients sont recensés et suivis par la RSSI, qui en vérifie la version en vigueur.
- **Conservation.** Les enregistrements du SMSI sont conservés au moins trois ans, soit la durée d'un cycle de certification, sauf obligation légale ou contractuelle plus longue.

> Dans ce dépôt de démonstration, l'historique Git tient lieu d'historique des versions.

## 6. Registre des documents du SMSI

| Référence | Document | Exigence | Version | Classification | Statut |
|---|---|---|---|---|---|
| NTG-SMSI-DOC-001 | Maîtrise des informations documentées | 7.5 | 1.0 | Interne | Approuvé |
| NTG-SMSI-CTX-001 | Présentation de NotAge | 4.1 | 1.0 | Interne | Approuvé |
| NTG-SMSI-CTX-002 | Enjeux et parties intéressées | 4.1, 4.2 | 1.0 | Interne | Approuvé |
| NTG-SMSI-CTX-003 | Périmètre du SMSI | 4.3 | 1.0 | Interne | Approuvé |
| NTG-SMSI-CTX-004 | Cartographie du SI et inventaire des actifs | 4.3, A.5.9 | 1.0 | Confidentiel | Approuvé |
| NTG-SMSI-POL-001 | Politique du SMSI | 5.2 | 1.0 | Interne | Approuvé |
| NTG-SMSI-GOV-001 | Organisation de la sécurité et matrice RACI | 5.3 | 1.0 | Interne | Approuvé |
| NTG-SMSI-RSK-001 | Méthodologie d'appréciation et de traitement des risques | 6.1.2, 6.1.3 | 1.0 | Interne | Approuvé |
| NTG-SMSI-RSK-002 | Registre des risques | 8.2 | 1.0 | Confidentiel | Approuvé |
| NTG-SMSI-RSK-003 | Rapport d'analyse de risques | 8.2 | 1.0 | Confidentiel | Approuvé |
| NTG-SMSI-RSK-004 | Plan de traitement des risques | 6.1.3, 8.3 | 1.0 | Confidentiel | Approuvé |
| NTG-SMSI-DDA-001 | Déclaration d'applicabilité | 6.1.3 d) | 1.0 | Interne | Approuvé |
| NTG-SMSI-PSSI-001 | Politique de sécurité des systèmes d'information | 5.2, 7.5.1 b) | 1.0 | Interne | Approuvé |
| NTG-SMSI-PRC-001 | Procédure de gestion des incidents | A.5.24 à A.5.28 | 1.0 | Interne | Approuvé |
| NTG-SMSI-PRC-002 | Procédure de gestion des accès | A.5.15 à A.5.18 | 1.0 | Interne | Approuvé |
| NTG-SMSI-PIL-001 | Objectifs et indicateurs de sécurité | 6.2, 9.1 | – | Interne | À produire |
| NTG-SMSI-AUD-001 | Rapport d'audit blanc | 9.2 | – | Confidentiel | À produire |
