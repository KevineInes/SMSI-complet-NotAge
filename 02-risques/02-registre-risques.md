# Registre des risques

| Référence | Version | Date | Propriétaire | Approbateur | Classification | Statut |
|---|---|---|---|---|---|---|
| NTG-SMSI-RSK-002 | 1.0 | 27/09/2026 | RSSI | Direction générale (CEO) | Confidentiel | Approuvé |

Exigences couvertes : ISO/IEC 27001:2022, articles 6.1.2 et 8.2. Méthode : [NTG-SMSI-RSK-001](01-methodologie-risques.md).

> Version de lecture du registre. Le fichier de référence est [`02-registre-risques.xlsx`](02-registre-risques.xlsx), qui contient les échelles, les formules de calcul et la cartographie.

## Synthèse

Le **risque initial** est évalué avec les mesures existantes en septembre 2026. Le **risque résiduel** est celui visé après le [plan de traitement](04-plan-traitement.md).

| ID | Scénario | DIC | G | V | Initial | Mesures de l'annexe A | Résiduel | Propriétaire |
|---|---|---|---|---|---|---|---|---|
| R01 | Détournement de paiements par modification frauduleuse d'un IBAN fournisseur | I | 4 | 3 | 🟥 12 | 8.26, 8.5, 8.15, 8.16 | 🟨 4 | CFO |
| R02 | Chiffrement ou destruction de la production par rançongiciel après compromission d'un compte administrateur AWS | D, I | 4 | 3 | 🟥 12 | 8.2, 5.18, 8.5, 8.13, 8.16, 5.24, 5.26 | 🟨 6 | CTO |
| R03 | Vol massif de données par exploitation d'une vulnérabilité de l'application | C | 4 | 3 | 🟥 12 | 8.8, 8.28, 8.29 | 🟧 8 | CTO |
| R04 | Exposition publique de justificatifs par erreur de configuration du stockage cloud | C | 4 | 2 | 🟧 8 | 8.9, 5.23, 8.16 | 🟨 4 | CTO |
| R05 | Injection de code malveillant ou vol de secrets via la chaîne de développement | I, C | 4 | 2 | 🟧 8 | 8.4, 5.17, 8.32, 8.28 | 🟨 4 | CTO |
| R06 | Consultation ou modification abusive de données clients par un membre du support | C, I | 3 | 2 | 🟨 6 | 8.3, 8.11, 8.15 | 🟩 3 | Responsable relation client |
| R07 | Utilisation du compte d'un ancien salarié resté actif | C | 3 | 3 | 🟧 9 | 5.16, 5.18, 6.5 | 🟩 3 | Responsable RH |
| R08 | Interruption prolongée du service en période de clôture comptable | D, I | 3 | 3 | 🟧 9 | 5.30, 8.13, 8.32 | 🟨 4 | CTO |
| R09 | Compromission d'un compte de messagerie par hameçonnage ciblé | C | 3 | 2 | 🟨 6 | 6.3, 6.8 | 🟨 4 | Direction générale (CEO) |
| R10 | Perte ou vol d'un ordinateur portable ou d'un smartphone personnel | C | 2 | 3 | 🟨 6 | 8.1, 7.9 | 🟩 3 | CTO |
| R11 | Fuite de données clients via un fournisseur SaaS compromis | C, I | 3 | 2 | 🟨 6 | 5.19, 5.20 | 🟩 3 | CFO |
| R12 | Accès aux données par une autorité étrangère via l'hébergeur (Cloud Act) | C | 3 | 1 | 🟩 3 | Acceptation | 🟩 3 | Direction générale (CEO) |

**Répartition initiale** : 3 critiques, 4 élevés, 4 modérés, 1 faible. **Après traitement** : aucun critique, 1 élevé accepté par la direction (R03), 6 modérés, 5 faibles.

![Cartographie des risques initiaux](img/cartographie-risques-initiaux.png)

## Détail des scénarios

### R01 — Détournement de paiements par modification frauduleuse d'un IBAN fournisseur

**Niveau initial : 🟥 12 (Critique)** · Gravité 4 · Vraisemblance 3 · Critère I · Propriétaire : CFO

| Élément | Description |
|---|---|
| Source de risque | Groupe cybercriminel spécialisé dans la fraude au virement |
| Scénario | L'attaquant obtient les identifiants d'un utilisateur d'une entreprise cliente (hameçonnage ou mot de passe réutilisé), se connecte à NotAge et remplace l'IBAN d'un fournisseur. Le fichier de virement suivant, validé sans vérification particulière, envoie les paiements sur son compte. |
| Actifs primordiaux | AP2, AP5 |
| Actifs supports | AS04, AS06 |
| Vulnérabilités | Authentification multifacteur non imposée aux utilisateurs clients ; modification d'IBAN sans contrôle renforcé ni notification ; aucune détection des comportements anormaux |
| Mesures existantes | Journal applicatif basique ; circuit de validation des factures (qui ne couvre pas le changement d'IBAN) |
| Justification de la gravité | Fraude pouvant atteindre plusieurs centaines de milliers d'euros chez un client, mise en cause de NotAge, perte probable du client |
| Justification de la vraisemblance | Fraude très active en France, vecteur simple, aucune mesure ne bloque la modification |
| Traitement | Réduire — mesures 8.26, 8.5, 8.15, 8.16 ; échéance 31/12/2026 |
| Risque résiduel | 🟨 4 (Modéré), G4 × V1 — Acceptée par le CFO |

### R02 — Chiffrement ou destruction de la production par rançongiciel après compromission d'un compte administrateur AWS

**Niveau initial : 🟥 12 (Critique)** · Gravité 4 · Vraisemblance 3 · Critère D, I · Propriétaire : CTO

| Élément | Description |
|---|---|
| Source de risque | Groupe cybercriminel (rançongiciel) |
| Scénario | L'attaquant vole les accès de l'un des dix comptes à privilèges étendus (hameçonnage, clé d'accès exposée sur un poste). Il chiffre ou supprime les bases et le stockage, efface les sauvegardes accessibles avec les mêmes droits, puis exige une rançon. |
| Actifs primordiaux | AP1 à AP5 |
| Actifs supports | AS01, AS02, AS06, AS12 |
| Vulnérabilités | Droits d'administration étendus à dix personnes sans revue ; sauvegardes supprimables avec les mêmes droits et restauration jamais testée ; pas de surveillance centralisée ; pas de procédure de réponse aux incidents |
| Mesures existantes | Authentification multifacteur sur la console via le SSO (pas sur les clés d'accès programmatiques) ; sauvegardes automatiques répliquées dans une autre région |
| Justification de la gravité | Arrêt complet du service pour tous les clients pendant plusieurs jours, perte de données possible, manquement contractuel généralisé |
| Justification de la vraisemblance | Les rançongiciels ciblent massivement les PME ; dix comptes à privilèges sans revue multiplient les points d'entrée |
| Traitement | Réduire et partager — mesures 8.2, 5.18, 8.5, 8.13, 8.16, 5.24, 5.26 ; échéance 31/12/2026 |
| Risque résiduel | 🟨 6 (Modéré), G3 × V2 — Acceptée par le CTO |

### R03 — Vol massif de données par exploitation d'une vulnérabilité de l'application

**Niveau initial : 🟥 12 (Critique)** · Gravité 4 · Vraisemblance 3 · Critère C · Propriétaire : CTO

| Élément | Description |
|---|---|
| Source de risque | Cybercriminels (revente de données, extorsion) |
| Scénario | Un attaquant exploite une vulnérabilité de l'application ou de l'API, par exemple un défaut de cloisonnement entre clients relevé lors du test d'intrusion de 2025 et non corrigé, pour extraire en masse justificatifs, identités et IBAN d'autres clients. |
| Actifs primordiaux | AP1, AP3 |
| Actifs supports | AS04, AS05 |
| Vulnérabilités | Vulnérabilités du test d'intrusion de 2025 pas toutes corrigées ; pas de processus de gestion des vulnérabilités ; pas de tests de sécurité automatisés dans la chaîne CI/CD ; pas de règles de codage sécurisé formalisées |
| Mesures existantes | Revue de code systématique ; pare-feu applicatif |
| Justification de la gravité | Violation massive de données personnelles, notification par tous les clients à la CNIL, sanctions possibles, atteinte durable à l'image |
| Justification de la vraisemblance | Vulnérabilités connues et non corrigées sur une application exposée sur Internet |
| Traitement | Réduire — mesures 8.8, 8.28, 8.29 ; échéance 31/12/2026 (corrections), 31/03/2027 (outillage) |
| Risque résiduel | 🟧 8 (Élevé), G4 × V2 — Risque résiduel élevé accepté par écrit par la direction générale jusqu'au test d'intrusion de mars 2027 |

### R04 — Exposition publique de justificatifs par erreur de configuration du stockage cloud

**Niveau initial : 🟧 8 (Élevé)** · Gravité 4 · Vraisemblance 2 · Critère C · Propriétaire : CTO

| Élément | Description |
|---|---|
| Source de risque | Erreur interne non intentionnelle |
| Scénario | Lors d'une évolution, un espace de stockage de justificatifs ou un instantané de base de données est rendu accessible publiquement. L'exposition est découverte par un chercheur en sécurité ou par un attaquant qui scanne Internet. |
| Actifs primordiaux | AP1 |
| Actifs supports | AS01 |
| Vulnérabilités | Pas de référentiel de configuration sécurisée ni de contrôle automatique des configurations ; infrastructure modifiée manuellement par plusieurs personnes ; aucune alerte en cas de changement risqué |
| Mesures existantes | Chiffrement au repos (sans effet en cas d'exposition publique) |
| Justification de la gravité | Exposition potentielle de l'ensemble des justificatifs des utilisateurs, violation de données notifiable |
| Justification de la vraisemblance | Erreur fréquente dans le secteur, mais qui suppose un changement de configuration malheureux |
| Traitement | Réduire — mesures 8.9, 5.23, 8.16 ; échéance 31/03/2027 |
| Risque résiduel | 🟨 4 (Modéré), G4 × V1 — Acceptée par le CTO |

### R05 — Injection de code malveillant ou vol de secrets via la chaîne de développement

**Niveau initial : 🟧 8 (Élevé)** · Gravité 4 · Vraisemblance 2 · Critère I, C · Propriétaire : CTO

| Élément | Description |
|---|---|
| Source de risque | Cybercriminels (attaque de la chaîne d'approvisionnement logicielle) |
| Scénario | L'attaquant compromet le compte GitHub d'un développeur ou une dépendance tierce. Il fait déployer du code malveillant en production ou récupère les secrets de production présents dans le code et la chaîne CI/CD. |
| Actifs primordiaux | AP6, AP4 |
| Actifs supports | AS05, AS13 |
| Vulnérabilités | Secrets présents dans le code et les variables de la CI ; authentification multifacteur GitHub non imposée à tous ; dépendances et actions tierces non contrôlées ; protections de branches incomplètes |
| Mesures existantes | Revue de code systématique avant fusion |
| Justification de la gravité | Code compromis distribué à tous les clients, accès complet à la production |
| Justification de la vraisemblance | Attaques de ce type en forte hausse, mais plus exigeantes techniquement ; la revue de code freine l'injection directe |
| Traitement | Réduire — mesures 8.4, 5.17, 8.32, 8.28 ; échéance 31/03/2027 |
| Risque résiduel | 🟨 4 (Modéré), G4 × V1 — Acceptée par le CTO |

### R06 — Consultation ou modification abusive de données clients par un membre du support

**Niveau initial : 🟨 6 (Modéré)** · Gravité 3 · Vraisemblance 2 · Critère C, I · Propriétaire : Responsable relation client

| Élément | Description |
|---|---|
| Source de risque | Salarié malveillant ou manipulé (interne) |
| Scénario | Un agent du support, qui dispose d'un accès complet au back-office, consulte des données sans besoin (curiosité, revente) ou modifie des coordonnées à la demande d'un faux client (ingénierie sociale). |
| Actifs primordiaux | AP1 à AP3 |
| Actifs supports | AS14, AS04 |
| Vulnérabilités | Accès au back-office non limité aux dossiers traités ; IBAN affichés en clair ; consultations ni journalisées ni revues |
| Mesures existantes | Clause de confidentialité dans les contrats de travail |
| Justification de la gravité | Atteinte aux données de plusieurs clients, possible complicité de fraude |
| Justification de la vraisemblance | Équipe de huit personnes de confiance, mais aucune barrière technique ni traçabilité |
| Traitement | Réduire — mesures 8.3, 8.11, 8.15 ; échéance 31/03/2027 |
| Risque résiduel | 🟩 3 (Faible), G3 × V1 — Acceptée par le responsable relation client |

### R07 — Utilisation du compte d'un ancien salarié resté actif

**Niveau initial : 🟧 9 (Élevé)** · Gravité 3 · Vraisemblance 3 · Critère C · Propriétaire : Responsable RH

| Élément | Description |
|---|---|
| Source de risque | Ancien salarié mécontent, ou attaquant réutilisant des identifiants |
| Scénario | Les comptes d'un salarié parti (Google Workspace, AWS, GitHub, outils SaaS) n'ont pas tous été désactivés. Ils sont utilisés pour accéder à des données internes ou clients. |
| Actifs primordiaux | AP1, AP6, AP7 |
| Actifs supports | AS06 |
| Vulnérabilités | Départs gérés sans procédure ni liste des accès à retirer ; pas de revue périodique des comptes ; plusieurs outils SaaS hors du SSO |
| Mesures existantes | Désactivation du compte Google à la demande des RH, de façon irrégulière |
| Justification de la gravité | Accès non autorisé à des données clients ou au code |
| Justification de la vraisemblance | Comptes orphelins déjà constatés à l'arrivée de la RSSI ; vingt départs et arrivées attendus avec la croissance |
| Traitement | Réduire — mesures 5.16, 5.18, 6.5 ; échéance 31/12/2026 |
| Risque résiduel | 🟩 3 (Faible), G3 × V1 — Acceptée par la responsable RH |

### R08 — Interruption prolongée du service en période de clôture comptable

**Niveau initial : 🟧 9 (Élevé)** · Gravité 3 · Vraisemblance 3 · Critère D, I · Propriétaire : CTO

| Élément | Description |
|---|---|
| Source de risque | Erreur humaine (déploiement), défaillance technique ou panne d'un service AWS |
| Scénario | Une mise en production défaillante corrompt des données ou rend la plateforme indisponible en fin de mois. Faute de procédure de retour arrière et de restauration éprouvée, l'interruption dure plusieurs heures en pleine clôture. |
| Actifs primordiaux | AP4, AP5 |
| Actifs supports | AS01, AS02, AS04, AS05 |
| Vulnérabilités | Pas de plan de continuité ni de reprise ; restauration jamais testée ; gestion des changements informelle, sans plan de retour arrière ; objectifs de reprise non définis |
| Mesures existantes | Plateforme répartie sur plusieurs zones de disponibilité AWS ; sauvegardes automatiques |
| Justification de la gravité | Engagement de disponibilité de 99,9 % rompu, clôtures des clients retardées, pénalités possibles |
| Justification de la vraisemblance | Plusieurs mises en production par semaine sans filet ; un incident de ce type est attendu dans l'année |
| Traitement | Réduire — mesures 5.30, 8.13, 8.32 ; échéance 31/03/2027 |
| Risque résiduel | 🟨 4 (Modéré), G2 × V2 — Acceptée par le CTO |

### R09 — Compromission d'un compte de messagerie par hameçonnage ciblé

**Niveau initial : 🟨 6 (Modéré)** · Gravité 3 · Vraisemblance 2 · Critère C · Propriétaire : Direction générale (CEO)

| Élément | Description |
|---|---|
| Source de risque | Cybercriminels |
| Scénario | Une fausse page de connexion Google capture l'identifiant et le code de double authentification d'un salarié (attaque par relais). L'attaquant accède à ses e-mails et documents (contrats, exports clients) et s'en sert pour hameçonner des clients au nom de NotAge. |
| Actifs primordiaux | AP7, AP1 |
| Actifs supports | AS07, AS09 |
| Vulnérabilités | Aucune sensibilisation des salariés ; pas de procédure de signalement ; double authentification par code, non résistante au hameçonnage |
| Mesures existantes | Authentification multifacteur sur Google Workspace ; filtrage anti-spam natif |
| Justification de la gravité | Fuite de documents internes et clients, rebond possible vers les clients |
| Justification de la vraisemblance | Hameçonnage omniprésent, mais la double authentification impose une attaque plus élaborée |
| Traitement | Réduire — mesures 6.3, 6.8 ; échéance 31/12/2026 |
| Risque résiduel | 🟨 4 (Modéré), G2 × V2 — Acceptée par la direction générale |

### R10 — Perte ou vol d'un ordinateur portable ou d'un smartphone personnel

**Niveau initial : 🟨 6 (Modéré)** · Gravité 2 · Vraisemblance 3 · Critère C · Propriétaire : CTO

| Élément | Description |
|---|---|
| Source de risque | Vol opportuniste ou perte |
| Scénario | Un smartphone personnel sans code de verrouillage, qui donne accès à la messagerie et à Slack (où circulent des captures de données clients), est volé. Ou un portable est perdu avec des sessions ouvertes. |
| Actifs primordiaux | AP7, AP1 |
| Actifs supports | AS09, AS10 |
| Vulnérabilités | Smartphones personnels non gérés (pas de code imposé, pas d'effacement à distance) ; pas de gestion centralisée des postes ; pas de règles pour les déplacements |
| Mesures existantes | Disques des ordinateurs portables chiffrés |
| Justification de la gravité | Exposition limitée aux données présentes sur l'appareil |
| Justification de la vraisemblance | Perte ou vol d'appareil très fréquent avec 50 salariés en télétravail et en déplacement |
| Traitement | Réduire — mesures 8.1, 7.9 ; échéance 31/03/2027 |
| Risque résiduel | 🟩 3 (Faible), G1 × V3 — Acceptée par le CTO |

### R11 — Fuite de données clients via un fournisseur SaaS compromis

**Niveau initial : 🟨 6 (Modéré)** · Gravité 3 · Vraisemblance 2 · Critère C, I · Propriétaire : CFO

| Élément | Description |
|---|---|
| Source de risque | Cybercriminels ciblant un fournisseur |
| Scénario | L'outil de support (dont les tickets contiennent des captures et des IBAN) ou le prestataire d'envoi d'e-mails transactionnels est compromis. Il en résulte une fuite de données clients ou l'envoi d'e-mails frauduleux au nom de NotAge. |
| Actifs primordiaux | AP1 |
| Actifs supports | AS08, AS16 |
| Vulnérabilités | Fournisseurs jamais évalués ; contrats sans clauses de sécurité ni obligation de notifier les incidents ; données sensibles copiées sans nécessité dans les tickets |
| Mesures existantes | Aucune mesure spécifique |
| Justification de la gravité | Violation de données notifiable, manquement aux clauses DORA des clients financiers |
| Justification de la vraisemblance | Attaques contre les éditeurs SaaS en hausse ; fournisseurs établis mais non évalués |
| Traitement | Réduire — mesures 5.19, 5.20 ; échéance 30/06/2027 |
| Risque résiduel | 🟩 3 (Faible), G3 × V1 — Acceptée par le CFO |

### R12 — Accès aux données par une autorité étrangère via l'hébergeur (Cloud Act)

**Niveau initial : 🟩 3 (Faible)** · Gravité 3 · Vraisemblance 1 · Critère C · Propriétaire : Direction générale (CEO)

| Élément | Description |
|---|---|
| Source de risque | Autorité étatique étrangère (droit extraterritorial) |
| Scénario | Une autorité américaine contraint AWS à communiquer des données hébergées, sans que NotAge ni ses clients en soient informés. |
| Actifs primordiaux | AP1 à AP3 |
| Actifs supports | AS15 |
| Vulnérabilités | Hébergeur soumis au droit américain ; clés de chiffrement gérées par l'hébergeur |
| Mesures existantes | Données hébergées en France ; chiffrement au repos ; engagements contractuels de l'hébergeur |
| Justification de la gravité | Question de confiance sensible pour les clients bancaires |
| Justification de la vraisemblance | Données de gestion de dépenses sans intérêt particulier pour une autorité étrangère ; cas jamais observé pour ce type de données |
| Traitement | Accepter — mesures aucune nouvelle mesure ; échéance Revue annuelle |
| Risque résiduel | 🟩 3 (Faible), G3 × V1 — Acceptée par la direction générale |
