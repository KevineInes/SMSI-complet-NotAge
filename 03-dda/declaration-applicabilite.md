# Déclaration d'applicabilité (DdA)

| Référence | Version | Date | Propriétaire | Approbateur | Classification | Statut |
|---|---|---|---|---|---|---|
| NTG-SMSI-DDA-001 | 1.0 | 27/09/2026 | RSSI | Direction générale (CEO) | Interne | Approuvé |

Exigence couverte : ISO/IEC 27001:2022, article 6.1.3 d). Fichier de référence : [`declaration-applicabilite.xlsx`](declaration-applicabilite.xlsx).

## Synthèse

| Thème | Mesures | Applicables | Exclues | Mesures prioritaires |
|---|---|---|---|---|
| A.5 Organisationnelles | 37 | 37 | 0 | 9 |
| A.6 Liées aux personnes | 8 | 8 | 0 | 3 |
| A.7 Physiques | 14 | 12 | 2 | 1 |
| A.8 Technologiques | 34 | 33 | 1 | 15 |
| **Total** | **93** | **90** | **3** | **28** |

État de mise en œuvre des 90 mesures applicables :

- ✅ 26 mises en œuvre ;
- 🟡 25 partielles ;
- 🔵 39 planifiées.

**Comment lire cette DdA**

- **Toutes les mesures sont examinées.** Les 93 mesures de l'annexe A sont passées en revue, et chaque inclusion comme chaque exclusion est justifiée.
- **Les mesures prioritaires.** Les **28 mesures prioritaires** (★) sont celles que le [plan de traitement](../02-risques/04-plan-traitement.md) retient pour traiter les 12 scénarios de risque.
- **Les autres mesures applicables.** Elles découlent d'exigences légales, d'exigences contractuelles ou du fonctionnement du SMSI.

| Code | Signification |
|---|---|
| Rxx | Réduit le scénario de risque Rxx |
| LEG | Exigence légale ou réglementaire |
| CTR | Exigence contractuelle (clients, clauses DORA) |
| SMSI | Exigence du système de management ou bonne pratique |

## Mesures exclues

| Mesure | Justification de l'exclusion |
|---|---|
| **7.6** Travail dans les zones sécurisées | Aucune zone sécurisée dans les locaux : aucun équipement de production n'y est hébergé. La sécurité physique des centres de données relève d'AWS et est maîtrisée par les mesures 5.19 à 5.23. |
| **7.12** Sécurité du câblage | Câblage de l'immeuble géré par le bailleur ; les locaux n'hébergent que des postes de travail et aucun flux de production n'y transite. |
| **8.30** Développement externalisé | NotAge ne sous-traite aucun développement. Mesure à réévaluer en cas de recours à un prestataire. |

## A.5 — Mesures organisationnelles

| Mesure | Intitulé | Appl. | Justification | Sources | Statut | Réf. |
|---|---|---|---|---|---|---|
| **5.1** | Politiques de sécurité de l'information | Oui | Politique du SMSI et PSSI approuvées par la direction et déclinées en procédures. | SMSI | ✅ Mise en œuvre | POL-001, PSSI |
| **5.2** | Fonctions et responsabilités liées à la sécurité de l'information | Oui | Rôles, comité de sécurité et matrice RACI définis et communiqués. | SMSI | ✅ Mise en œuvre | GOV-001 |
| **5.3** | Séparation des tâches | Oui | La RSSI n'administre pas la production ; aucun déploiement sans validation d'un tiers. | R02, R05 | 🟡 Partielle | GOV-001, PSSI §8 |
| **5.4** | Responsabilités de la direction | Oui | La direction exige de tous les salariés et prestataires l'application de la PSSI. | SMSI | ✅ Mise en œuvre | POL-001 |
| **5.5** | Contacts avec les autorités | Oui | Contacts identifiés : CNIL (violations de données), ANSSI et CERT-FR, forces de l'ordre (fraude). | LEG | 🟡 Partielle | PRC-001 |
| **5.6** | Contacts avec des groupes d'intérêt spécifiques | Oui | Abonnement aux alertes du CERT-FR et participation à un club de RSSI. | SMSI | 🔵 Planifiée | PSSI §2 |
| **5.7** | Renseignement sur les menaces | Oui | Veille sur les menaces visant les éditeurs SaaS et la fraude au virement, intégrée à l'appréciation des risques. | R01, R03 | 🔵 Planifiée | RSK-001 |
| **5.8** | Sécurité de l'information dans la gestion de projet | Oui | Analyse de sécurité au lancement de toute fonctionnalité sensible. | R03 | 🔵 Planifiée | PSSI §8 |
| **5.9** | Inventaire des informations et autres actifs associés | Oui | Inventaire des actifs primordiaux et supports, avec leurs propriétaires. | SMSI | ✅ Mise en œuvre | CTX-004 |
| **5.10** | Utilisation correcte des informations et autres actifs associés | Oui | Charte d'utilisation des moyens informatiques annexée au règlement intérieur. | R09, R10 | 🔵 Planifiée | PSSI §6 |
| **5.11** | Restitution des actifs | Oui | Restitution du matériel vérifiée lors de chaque départ. | R07 | 🟡 Partielle | PRC-002 |
| **5.12** | Classification des informations | Oui | Quatre niveaux de classification définis. | SMSI, LEG | ✅ Mise en œuvre | DOC-001, PSSI §3 |
| **5.13** | Marquage des informations | Oui | Classification indiquée dans l'en-tête de chaque document. | SMSI | ✅ Mise en œuvre | DOC-001 |
| **5.14** | Transfert des informations | Oui | Échanges avec les clients chiffrés (HTTPS, API authentifiées), règles d'envoi des données sensibles. | R11, CTR | 🟡 Partielle | PSSI §3 |
| **5.15** | Contrôle d'accès | Oui | Accès fondés sur le besoin d'en connaître et le moindre privilège. | R06, R07 | 🟡 Partielle | PSSI §5, PRC-002 |
| **5.16** ★ | Gestion des identités | Oui | Identité unique par personne, outils raccordés au SSO, cycle de vie des comptes maîtrisé. | R07 | 🔵 Planifiée | PRC-002 |
| **5.17** ★ | Informations d'authentification | Oui | Secrets techniques stockés dans un coffre et renouvelés ; règles de mots de passe. | R05 | 🔵 Planifiée | PSSI §5 |
| **5.18** ★ | Droits d'accès | Oui | Droits validés par le manager, revue trimestrielle. | R02, R07 | 🔵 Planifiée | PRC-002 |
| **5.19** ★ | Sécurité de l'information dans les relations avec les fournisseurs | Oui | Fournisseurs classés par criticité et évalués sur le plan de la sécurité. | R11, CTR | 🔵 Planifiée | PSSI §9 |
| **5.20** ★ | Sécurité de l'information dans les accords avec les fournisseurs | Oui | Clauses de sécurité, notification des incidents, droit d'audit, réversibilité. | R11, CTR | 🔵 Planifiée | PSSI §9 |
| **5.21** | Gestion de la sécurité dans la chaîne d'approvisionnement TIC | Oui | Suivi des composants logiciels tiers et des sous-traitants des fournisseurs critiques (exigence DORA des clients). | R05, CTR | 🟡 Partielle | PSSI §9 |
| **5.22** | Surveillance, revue et gestion des changements des services fournisseurs | Oui | Revue annuelle des fournisseurs critiques : certifications, incidents, changements. | R11, CTR | 🔵 Planifiée | PSSI §9 |
| **5.23** ★ | Sécurité de l'information dans l'utilisation de services en nuage | Oui | Règles d'utilisation d'AWS, responsabilité partagée, configurations de référence. | R04, R12 | 🔵 Planifiée | PSSI §7, §9 |
| **5.24** ★ | Planification et préparation de la gestion des incidents | Oui | Procédure de gestion des incidents : rôles, contacts, grille de gravité. | R02, LEG, CTR | 🔵 Planifiée | PRC-001 |
| **5.25** | Appréciation des événements et prise de décision | Oui | Qualification de chaque événement selon une grille de gravité. | R02, CTR | 🔵 Planifiée | PRC-001 |
| **5.26** ★ | Réponse aux incidents de sécurité de l'information | Oui | Réponse documentée, notification des clients dans les délais contractuels. | R02 | 🔵 Planifiée | PRC-001 |
| **5.27** | Tirer des enseignements des incidents | Oui | Retour d'expérience après chaque incident significatif. | SMSI | 🔵 Planifiée | PRC-001 |
| **5.28** | Recueil de preuves | Oui | Conservation des journaux et des preuves en cas de fraude ou de dépôt de plainte. | LEG | 🔵 Planifiée | PRC-001 |
| **5.29** | Sécurité de l'information durant une perturbation | Oui | Maintien des mesures de sécurité en mode dégradé. | R08 | 🔵 Planifiée | PSSI §11 |
| **5.30** ★ | Préparation des TIC pour la continuité d'activité | Oui | Objectifs de reprise fixés (4 h, perte d'une heure au plus), plan de reprise testé chaque année. | R08 | 🔵 Planifiée | PSSI §11 |
| **5.31** | Exigences légales, statutaires, réglementaires et contractuelles | Oui | Exigences recensées : RGPD, clauses DORA des clients, veille NIS2. | LEG, CTR | ✅ Mise en œuvre | CTX-002 |
| **5.32** | Droits de propriété intellectuelle | Oui | Licences logicielles et composants open source suivis. | LEG | 🟡 Partielle | PSSI §12 |
| **5.33** | Protection des enregistrements | Oui | Enregistrements protégés et conservés au moins trois ans. | LEG, SMSI | ✅ Mise en œuvre | DOC-001 |
| **5.34** | Protection de la vie privée et des données à caractère personnel | Oui | DPO, registre des traitements, accords de sous-traitance, analyses d'impact. | LEG | 🟡 Partielle | PSSI §12 |
| **5.35** | Revue indépendante de la sécurité de l'information | Oui | Audit interne annuel confié à un prestataire externe. | SMSI | 🔵 Planifiée | GOV-001 |
| **5.36** | Conformité aux politiques, règles et normes de sécurité | Oui | Contrôles de conformité par les managers et la RSSI, suivis en comité de sécurité. | SMSI | 🔵 Planifiée | PIL-001 |
| **5.37** | Procédures d'exploitation documentées | Oui | Procédures de déploiement, de sauvegarde et de restauration documentées. | R08 | 🟡 Partielle | PSSI §7 |

## A.6 — Mesures liées aux personnes

| Mesure | Intitulé | Appl. | Justification | Sources | Statut | Réf. |
|---|---|---|---|---|---|---|
| **6.1** | Sélection des candidats | Oui | Vérifications proportionnées au poste, dans le respect du droit du travail. | LEG | 🟡 Partielle | PSSI §4 |
| **6.2** | Termes et conditions du contrat de travail | Oui | Clauses de sécurité et de confidentialité dans les contrats de travail. | SMSI | ✅ Mise en œuvre | PSSI §4 |
| **6.3** ★ | Sensibilisation, enseignement et formation | Oui | Sensibilisation à l'arrivée et annuelle, hameçonnage simulé, formation des développeurs. | R09 | 🔵 Planifiée | PSSI §4 |
| **6.4** | Processus disciplinaire | Oui | Sanctions prévues au règlement intérieur. | SMSI | ✅ Mise en œuvre | POL-001 |
| **6.5** ★ | Responsabilités après la fin ou la modification du contrat | Oui | Rappel des obligations de confidentialité et retrait des accès au départ. | R07 | 🔵 Planifiée | PRC-002 |
| **6.6** | Engagements de confidentialité ou de non-divulgation | Oui | Engagements de confidentialité signés par les salariés et les prestataires. | R06, CTR | ✅ Mise en œuvre | PSSI §4 |
| **6.7** | Travail à distance | Oui | Règles de télétravail : réseau, confidentialité, poste géré. | R10 | 🟡 Partielle | PSSI §6 |
| **6.8** ★ | Déclaration des événements de sécurité de l'information | Oui | Canal de signalement unique et simple, connu de tous les salariés. | R09 | 🔵 Planifiée | PRC-001 |

## A.7 — Mesures physiques

| Mesure | Intitulé | Appl. | Justification | Sources | Statut | Réf. |
|---|---|---|---|---|---|---|
| **7.1** | Périmètres de sécurité physique | Oui | Bureaux situés dans un immeuble à accès contrôlé. | SMSI | ✅ Mise en œuvre | PSSI §6 |
| **7.2** | Entrées physiques | Oui | Accès par badge nominatif, visiteurs enregistrés et accompagnés. | SMSI | ✅ Mise en œuvre | PSSI §6 |
| **7.3** | Sécurisation des bureaux, des salles et des installations | Oui | Bureaux fermés à clé en dehors des heures ouvrées. | SMSI | ✅ Mise en œuvre | PSSI §6 |
| **7.4** | Surveillance de la sécurité physique | Oui | Vidéosurveillance et alarme de l'immeuble gérées par le bailleur. | SMSI | ✅ Mise en œuvre | PSSI §6 |
| **7.5** | Protection contre les menaces physiques et environnementales | Oui | Indisponibilité des locaux (crue, canicule) couverte par le télétravail. | R08 | 🟡 Partielle | PSSI §11 |
| **7.6** | Travail dans les zones sécurisées | **Non** | Aucune zone sécurisée dans les locaux : aucun équipement de production n'y est hébergé. La sécurité physique des centres de données relève d'AWS et est maîtrisée par les mesures 5.19 à 5.23. | — | ⛔ Non applicable | — |
| **7.7** | Bureau propre et écran vide | Oui | Verrouillage automatique des sessions, aucun document sensible laissé sur les bureaux. | R10 | 🟡 Partielle | PSSI §6 |
| **7.8** | Emplacement et protection du matériel | Oui | Équipement réseau des bureaux dans une baie fermée à clé. | SMSI | ✅ Mise en œuvre | PSSI §6 |
| **7.9** ★ | Sécurité des actifs hors des locaux | Oui | Règles de protection des appareils en déplacement, déclaration de perte sous 24 h. | R10 | 🔵 Planifiée | PSSI §6 |
| **7.10** | Supports de stockage | Oui | Supports amovibles déconseillés, chiffrés lorsqu'ils sont indispensables. | R10 | 🟡 Partielle | PSSI §6 |
| **7.11** | Services supports | Oui | Connexion Internet de secours pour les bureaux ; la plateforme n'en dépend pas. | SMSI | ✅ Mise en œuvre | PSSI §11 |
| **7.12** | Sécurité du câblage | **Non** | Câblage de l'immeuble géré par le bailleur ; les locaux n'hébergent que des postes de travail et aucun flux de production n'y transite. | — | ⛔ Non applicable | — |
| **7.13** | Maintenance du matériel | Oui | Maintenance des portables par le fournisseur, après effacement ou sous contrôle. | SMSI | ✅ Mise en œuvre | PSSI §6 |
| **7.14** | Élimination ou recyclage sécurisé du matériel | Oui | Effacement certifié des disques avant recyclage ou réattribution. | LEG | 🟡 Partielle | PSSI §6 |

## A.8 — Mesures technologiques

| Mesure | Intitulé | Appl. | Justification | Sources | Statut | Réf. |
|---|---|---|---|---|---|---|
| **8.1** ★ | Terminaux des utilisateurs | Oui | Gestion centralisée des portables et accès mobile via un profil professionnel protégé. | R10 | 🔵 Planifiée | PSSI §6 |
| **8.2** ★ | Droits d'accès privilégiés | Oui | Deux administrateurs permanents, élévation temporaire sur demande, clés de sécurité physiques. | R02 | 🔵 Planifiée | PRC-002 |
| **8.3** ★ | Restriction d'accès aux informations | Oui | Accès du support limité aux clients ayant ouvert une demande. | R06 | 🔵 Planifiée | PSSI §5 |
| **8.4** ★ | Accès au code source | Oui | Accès GitHub selon le besoin, authentification multifacteur obligatoire, branches protégées. | R05 | 🔵 Planifiée | PSSI §8 |
| **8.5** ★ | Authentification sécurisée | Oui | Authentification multifacteur pour tous les salariés, obligatoire pour les rôles sensibles des clients, résistante à l'hameçonnage pour les administrateurs. | R01, R02 | 🟡 Partielle | PSSI §5 |
| **8.6** | Dimensionnement | Oui | Mise à l'échelle automatique et suivi de la capacité, notamment pendant les clôtures. | R08 | ✅ Mise en œuvre | PSSI §7 |
| **8.7** | Protection contre les programmes malveillants | Oui | Protection des postes et analyse des justificatifs téléversés. | R02, R09 | 🟡 Partielle | PSSI §6 |
| **8.8** ★ | Gestion des vulnérabilités techniques | Oui | Correction selon des délais par criticité, suivi des vulnérabilités du test d'intrusion. | R03 | 🔵 Planifiée | PSSI §7 |
| **8.9** ★ | Gestion des configurations | Oui | Infrastructure décrite en code, configurations de référence, contrôle automatique. | R04 | 🔵 Planifiée | PSSI §7 |
| **8.10** | Suppression des informations | Oui | Suppression des données des clients en fin de contrat selon les durées convenues. | LEG, CTR | 🟡 Partielle | PSSI §12 |
| **8.11** ★ | Masquage des données | Oui | IBAN masqués dans le back-office et dans les environnements de test. | R06 | 🔵 Planifiée | PSSI §5 |
| **8.12** | Prévention de la fuite de données | Oui | Détection des exports massifs et des données sensibles copiées dans les tickets. | R03, R11 | 🔵 Planifiée | PSSI §7 |
| **8.13** ★ | Sauvegarde des informations | Oui | Sauvegardes chiffrées et immuables dans un compte séparé, restauration testée chaque trimestre. | R02, R08 | 🟡 Partielle | PSSI §7 |
| **8.14** | Redondance des moyens de traitement de l'information | Oui | Plateforme répartie sur plusieurs zones de disponibilité AWS. | R08 | ✅ Mise en œuvre | PSSI §11 |
| **8.15** ★ | Journalisation | Oui | Journaux applicatifs et d'infrastructure centralisés, protégés et conservés un an. | R01, R06 | 🔵 Planifiée | PSSI §7 |
| **8.16** ★ | Activités de surveillance | Oui | Détection des comportements anormaux et alertes sur les actions sensibles. | R01, R02, R04 | 🔵 Planifiée | PSSI §7 |
| **8.17** | Synchronisation des horloges | Oui | Services synchronisés sur une source de temps de référence. | SMSI | ✅ Mise en œuvre | PSSI §7 |
| **8.18** | Utilisation de programmes utilitaires à privilèges | Oui | Outils d'administration réservés aux administrateurs et journalisés. | R02 | 🟡 Partielle | PRC-002 |
| **8.19** | Installation de logiciels sur des systèmes en exploitation | Oui | Déploiement en production uniquement par la chaîne CI/CD. | R05 | 🟡 Partielle | PSSI §8 |
| **8.20** | Sécurité des réseaux | Oui | Réseaux privés AWS, règles de filtrage restrictives, bases de données non exposées à Internet. | R02 | ✅ Mise en œuvre | PSSI §7 |
| **8.21** | Sécurité des services réseau | Oui | Chiffrement TLS, pare-feu applicatif, protection contre le déni de service. | R03 | ✅ Mise en œuvre | PSSI §7 |
| **8.22** | Cloisonnement des réseaux | Oui | Production, hors production et administration séparées dans des comptes et réseaux distincts. | R02, R04 | 🟡 Partielle | PSSI §7 |
| **8.23** | Filtrage web | Oui | Filtrage des sites malveillants sur les postes gérés. | R09 | 🔵 Planifiée | PSSI §6 |
| **8.24** | Utilisation de la cryptographie | Oui | Chiffrement au repos et en transit, clés gérées par le service AWS dédié. | LEG, CTR, R12 | ✅ Mise en œuvre | PSSI §7 |
| **8.25** | Cycle de vie de développement sécurisé | Oui | Sécurité intégrée à chaque étape du développement. | R03, R05 | 🟡 Partielle | PSSI §8 |
| **8.26** ★ | Exigences de sécurité des applications | Oui | Double validation et notification des changements d'IBAN, réauthentification pour les actions sensibles. | R01 | 🔵 Planifiée | PSSI §8 |
| **8.27** | Principes d'ingénierie et d'architecture des systèmes sécurisés | Oui | Défense en profondeur et cloisonnement strict des données entre clients. | R03 | 🟡 Partielle | PSSI §8 |
| **8.28** ★ | Codage sécurisé | Oui | Règles de codage fondées sur l'OWASP, contrôle des dépendances, formation des développeurs. | R03, R05 | 🔵 Planifiée | PSSI §8 |
| **8.29** ★ | Tests de sécurité dans le développement et l'acceptation | Oui | Analyse du code et des dépendances dans la CI, test d'intrusion annuel. | R03 | 🔵 Planifiée | PSSI §8 |
| **8.30** | Développement externalisé | **Non** | NotAge ne sous-traite aucun développement. Mesure à réévaluer en cas de recours à un prestataire. | — | ⛔ Non applicable | — |
| **8.31** | Séparation des environnements de développement, de test et de production | Oui | Comptes AWS distincts pour la production et la recette. | R04, R06 | ✅ Mise en œuvre | PSSI §8 |
| **8.32** ★ | Gestion des changements | Oui | Changements validés et tracés, plan de retour arrière, gel pendant les clôtures. | R05, R08 | 🔵 Planifiée | PSSI §8 |
| **8.33** | Informations de test | Oui | Aucune donnée de production en test sans anonymisation. | LEG | 🟡 Partielle | PSSI §8 |
| **8.34** | Protection des systèmes d'information pendant les tests d'audit | Oui | Tests d'intrusion encadrés par une convention et planifiés hors des périodes de clôture. | SMSI | ✅ Mise en œuvre | PSSI §8 |
