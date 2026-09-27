# Enjeux et parties intéressées

| Référence | Version | Date | Propriétaire | Approbateur | Classification | Statut |
|---|---|---|---|---|---|---|
| NTG-SMSI-CTX-002 | 1.0 | 27/09/2026 | RSSI | Direction générale (CEO) | Interne | Approuvé |

Exigences couvertes : ISO/IEC 27001:2022, articles 4.1 et 4.2, amendement 1:2024.

## 1. Enjeux externes

| Domaine | Enjeu | Conséquence pour le SMSI |
|---|---|---|
| Réglementaire | **RGPD** : NotAge traite pour ses clients les données personnelles de leurs salariés, dont des IBAN et des justificatifs de dépenses. | Obligations de sous-traitant (article 28), notification des violations au client sans délai, registre des traitements. |
| Réglementaire | **DORA** : les clients financiers doivent imposer à leurs prestataires informatiques des clauses précises. | Engagements contractuels à tenir : notification des incidents, droit d'audit, localisation des données, continuité, réversibilité. |
| Réglementaire | **NIS2** : la directive cite le SaaS parmi les modèles de services d'informatique en nuage, et NotAge atteint le seuil de la moyenne entreprise (50 salariés). La loi française de transposition n'est pas définitivement adoptée à la date de ce document ; l'ANSSI a publié le Référentiel Cyber France (ReCyF) comme document de travail. | Applicabilité à confirmer (voir section 4). Veille réglementaire confiée à la RSSI. Le SMSI est conçu pour couvrir l'essentiel des exigences de la directive. |
| Marché | Les grands comptes exigent une certification ISO 27001 et multiplient les questionnaires de sécurité. | La certification devient une condition d'accès au marché. |
| Menaces | Hausse des rançongiciels, de l'hameçonnage ciblé et de la **fraude au changement de coordonnées bancaires** ; attaques via les fournisseurs et les chaînes de développement logiciel. | Menaces prioritaires pour l'analyse de risques. |
| Dépendance technologique | Plateforme entièrement hébergée chez AWS, fournisseur soumis au droit américain (Cloud Act). | Risque de dépendance et question de souveraineté posée par les clients bancaires. |
| Climat | Événements climatiques extrêmes en Île-de-France (crue majeure de la Seine, canicules) pouvant affecter les bureaux ou les centres de données de la région. | Enjeu jugé **pertinent** : pris en compte dans la continuité d'activité (télétravail, répartition sur plusieurs zones AWS, sauvegardes dans une autre région). |

## 2. Enjeux internes

| Enjeu | Conséquence pour le SMSI |
|---|---|
| Croissance rapide : une vingtaine de recrutements prévus d'ici fin 2027. | Intégration et départ des salariés à maîtriser (accès, sensibilisation). |
| Culture startup qui privilégie la vitesse de livraison. | Sécurité à intégrer dans les pratiques existantes, sans bloquer les équipes. |
| Dépendance à quelques personnes clés (CTO, équipe infrastructure de 3 personnes). | Risque de perte de compétences et de concentration des droits d'administration. |
| Maturité sécurité faible (voir la présentation de NotAge, section 6). | Nombreuses mesures à créer ou à formaliser. |
| Budget et ressources limités : une seule personne dédiée à la sécurité. | Priorisation par les risques indispensable, recours ponctuel à des prestataires. |
| Télétravail généralisé et smartphones personnels tolérés. | Sécurisation des accès distants et des terminaux. |

## 3. Parties intéressées et exigences

La dernière colonne indique quelles exigences sont **traitées par le SMSI**, comme le demande l'article 4.2 c).

| Partie intéressée | Attentes et exigences | Traitée par le SMSI |
|---|---|---|
| Clients du secteur financier | Certification ISO 27001, clauses DORA, réponses aux questionnaires, audits sur site | Oui |
| Autres clients (ETI, PME) | Accord de sous-traitance RGPD, disponibilité contractuelle de 99,9 %, confidentialité des données | Oui |
| Utilisateurs finaux (salariés des clients) | Protection de leurs données personnelles et de leurs coordonnées bancaires | Oui |
| Fournisseurs des clients | Fiabilité des coordonnées bancaires utilisées pour les payer | Oui |
| Direction et actionnaires | Croissance, absence d'incident majeur, certification comme levier commercial | Oui |
| Salariés | Outils sûrs et simples, protection de leurs données RH, règles claires | Oui |
| CNIL | Respect du RGPD, notification des violations de données dans les délais | Oui |
| ANSSI | Application de NIS2 si NotAge entre dans son champ | Oui, sous réserve de confirmation |
| AWS, GitHub, Google et autres fournisseurs | Respect de leurs conditions d'utilisation et du modèle de responsabilité partagée | Oui |
| Assureur cyber | Conditions de couverture : authentification multifacteur, sauvegardes isolées, gestion des incidents | Oui |
| Organisme certificateur | Conformité à ISO/IEC 27001:2022 | Oui |

> Aucune partie intéressée identifiée n'exprime à ce jour d'exigence liée au changement climatique. Ce point sera réexaminé lors de chaque revue de direction.

## 4. Rôles de NotAge au regard des réglementations

| Texte | Rôle de NotAge | Conséquence |
|---|---|---|
| RGPD | **Sous-traitante** pour les données des utilisateurs des clients ; **responsable de traitement** pour ses propres salariés, prospects et candidats | Deux régimes d'obligations à distinguer |
| DORA | **Prestataire tiers de services TIC** des clients financiers, non soumis directement au règlement | Obligations contractuelles reprises dans le SMSI |
| NIS2 | **Entité importante potentielle**, si l'offre SaaS est qualifiée de service d'informatique en nuage | Vérification sur la plateforme MonEspaceNIS2 de l'ANSSI, suivi de la loi de transposition |
