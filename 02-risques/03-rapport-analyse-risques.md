# Rapport d'analyse de risques

| Référence | Version | Date | Propriétaire | Approbateur | Classification | Statut |
|---|---|---|---|---|---|---|
| NTG-SMSI-RSK-003 | 1.0 | 27/09/2026 | RSSI | Direction générale (CEO) | Confidentiel | Approuvé |

Exigences couvertes : ISO/IEC 27001:2022, articles 6.1.2 et 8.2. Méthode : ISO/IEC 27005:2022 ([NTG-SMSI-RSK-001](01-methodologie-risques.md)). Détail des scénarios : [registre des risques](02-registre-risques.md).

## 1. Synthèse pour la direction

L'analyse a identifié **12 scénarios de risque**. Évalués avec les mesures existantes, ils se répartissent en **3 risques critiques**, **4 élevés**, **4 modérés** et **1 faible**. Selon les critères de NotAge, les sept risques critiques ou élevés exigent un traitement.

Les trois risques critiques menacent directement le cœur de la relation client :

- **R01 — Fraude au changement d'IBAN.** Un compte client compromis suffit à détourner des paiements, car rien ne contrôle la modification d'un IBAN.
- **R02 — Rançongiciel sur la production.** Dix comptes à privilèges étendus et des sauvegardes supprimables avec les mêmes droits exposent NotAge à un arrêt de plusieurs jours.
- **R03 — Vol massif de données.** Des vulnérabilités applicatives connues depuis le test d'intrusion de 2025 ne sont pas toutes corrigées.

Ces risques ne viennent pas d'une menace exceptionnelle. Ils viennent de **cinq faiblesses transverses** (section 5), qu'un nombre limité de mesures bien choisies peut corriger. Le plan de traitement proposé retient **28 mesures de l'annexe A**. Il supprime tous les risques critiques et ramène tous les risques au plus au niveau Modéré, sauf R03 : son risque résiduel élevé est accepté par écrit par la direction jusqu'au test d'intrusion de mars 2027.

**Décision attendue de la direction** : valider le plan de traitement (NTG-SMSI-RSK-004) et son budget en comité de sécurité.

## 2. Démarche

| Élément | Description |
|---|---|
| Périmètre | Périmètre du SMSI ([NTG-SMSI-CTX-003](../00-contexte/03-perimetre-smsi.md)) |
| Période | Septembre 2026 |
| Participants | Ateliers animés par la RSSI avec le CTO, le responsable infrastructure, le CFO, le responsable relation client, la responsable RH et le DPO |
| Données d'entrée | Inventaire des actifs, constat initial de sécurité, enjeux et parties intéressées, rapport du test d'intrusion de 2025, état de la menace publié par l'ANSSI et le CERT-FR |
| Validation | Comité de sécurité ; niveaux validés par chaque propriétaire de risque |

## 3. Cartographie des risques initiaux

![Cartographie des risques initiaux](img/cartographie-risques-initiaux.png)

| Zone | Scénarios |
|---|---|
| 🟥 Critique (12) | R01, R02, R03 |
| 🟧 Élevé (8 à 9) | R04, R05, R07, R08 |
| 🟨 Modéré (6) | R06, R09, R10, R11 |
| 🟩 Faible (3) | R12 |

La cartographie couvre les trois propriétés de sécurité :

- **Intégrité** : R01, R02, R05, R06, R08, R11.
- **Confidentialité** : R03, R04, R05, R06, R07, R09, R10, R11, R12.
- **Disponibilité** : R02, R08.

Elle couvre aussi toutes les familles de sources de risque : cybercriminels, internes malveillants ou négligents, erreurs, fournisseurs et autorités étrangères.

## 4. Analyse des risques prioritaires

### Les trois risques critiques

**R01 — Fraude au changement d'IBAN (G4 × V3)**

C'est le risque le plus spécifique à l'activité de NotAge, et celui que les clients bancaires redoutent le plus. Sa gravité tient au fait que l'attaque ne vise pas NotAge mais **l'argent de ses clients**, par l'intermédiaire de sa plateforme. L'intégrité de l'IBAN compte donc davantage que sa confidentialité.

La vraisemblance est forte pour deux raisons : la fraude au virement est très répandue, et le scénario ne demande qu'un mot de passe volé. Trois leviers changent la donne :

- imposer l'authentification forte pour les actions sensibles ;
- appliquer une double validation avec notification pour tout changement d'IBAN ;
- détecter les comportements anormaux.

**R02 — Rançongiciel après compromission d'un compte administrateur AWS (G4 × V3)**

Le point clé n'est pas l'absence de sauvegardes, mais leur **dépendance aux mêmes droits** que la production : un attaquant qui obtient un compte à privilèges peut tout supprimer d'un coup. S'y ajoute le fait qu'une restauration n'a jamais été testée, ce qui rend le délai de reprise inconnu.

Deux types de leviers réduisent ce risque :

- **réduire la vraisemblance** : limiter drastiquement les droits d'administration, surveiller les actions sensibles ;
- **réduire la gravité** : isoler et tester les sauvegardes, formaliser la réponse aux incidents.

**R03 — Vol massif de données via une vulnérabilité applicative (G4 × V3)**

Des vulnérabilités **connues et non corrigées** sur une application exposée sur Internet sont l'une des causes les plus fréquentes de violation de données. La revue de code existante ne suffit pas sans règles de codage sécurisé, tests de sécurité automatisés et processus de suivi des vulnérabilités.

### Les quatre risques élevés

| ID | Ce qui rend le risque élevé | Levier principal |
|---|---|---|
| R04 | Une seule erreur de configuration peut exposer tous les justificatifs, et rien ne la détecte | Configurations de référence et contrôle automatique |
| R05 | Des secrets de production dans le code, des accès GitHub hétérogènes | Gestion des secrets, contrôle des accès au code et des changements |
| R07 | Comptes orphelins déjà constatés, forte rotation attendue avec la croissance | Procédure de départ et revue périodique des accès |
| R08 | Mises en production fréquentes sans plan de retour arrière ni reprise testée | Continuité des TIC et gestion des changements |

### Les risques modérés et faible

Les risques modérés (R06, R09, R10, R11) seront traités, car les mesures sont peu coûteuses et plusieurs sont exigées par les clients financiers :

- sensibilisation ;
- gestion des terminaux ;
- clauses fournisseurs ;
- restriction et journalisation des accès du support.

Le risque **R12 (Cloud Act)** est faible : les données de gestion de dépenses présentent peu d'intérêt pour une autorité étrangère. Il est **proposé à l'acceptation** par la direction générale, avec une réponse prête pour les clients qui poseraient la question. Si un client l'exigeait, NotAge pourrait étudier une gestion de ses propres clés de chiffrement.

## 5. Causes racines transverses

Les 12 scénarios reposent sur cinq faiblesses communes. Les traiter à la racine est plus efficace que de traiter chaque scénario isolément.

| Cause racine | Scénarios concernés |
|---|---|
| **Identités et privilèges non maîtrisés** : droits étendus, départs mal gérés, accès du support sans limite | R02, R05, R06, R07 |
| **Absence de détection et de réponse** : pas de surveillance centralisée, pas de procédure d'incident | R01, R02, R04, R09 |
| **Sécurité applicative non outillée** : vulnérabilités non suivies, pas de tests de sécurité, secrets dans le code | R01, R03, R05 |
| **Résilience non éprouvée** : restauration jamais testée, pas de plan de continuité, changements informels | R02, R08 |
| **Facteur humain et fournisseurs ignorés** : aucune sensibilisation, terminaux personnels non gérés, fournisseurs non évalués | R09, R10, R11 |

## 6. Recommandations et suite

1. **Traiter en priorité les trois risques critiques**, avec un plan d'action sous trois mois, conformément aux critères d'acceptation.
2. **Structurer le plan de traitement autour des cinq causes racines** : c'est ainsi qu'on obtient un nombre limité de mesures (28) à fort effet.
3. **Présenter le plan en comité de sécurité**, avec les propriétaires des risques, pour approbation et acceptation formelle des risques résiduels.
4. **Réapprécier les risques** après la mise en œuvre des mesures prioritaires, puis au moins une fois par an.

## 7. Limites de l'analyse

- Il s'agit de la **première appréciation** des risques de NotAge. Les niveaux reposent sur des échelles qualitatives et sur le jugement des participants, et non sur une quantification financière.
- Les **risques stratégiques** non liés à la sécurité de l'information (concurrence, financement) sont hors du champ de cette analyse.
- L'analyse sera **enrichie** par les incidents à venir, les résultats des tests de sécurité et la veille sur la menace.
