# Références normatives

Ce guide s'appuie sur trois référentiels principaux. Ils sont **payants** et ne sont pas reproduits ici : les résumés ci-dessous sont rédigés avec nos propres mots. Pour toute exigence précise, consultez l'édition officielle.

## Les trois référentiels principaux

### IEC 62682 · Gestion de systèmes d'alarme dans les industries de transformation

- **Édition en vigueur** : 2.0, publiée en décembre 2022. Elle remplace l'édition 1.0 de 2014.
- **Langues** : anglais et français.
- **Ce qu'elle couvre** : principes et processus de gestion des alarmes présentées à l'opérateur par le système de conduite et l'IHM. Cela inclut les alarmes du système de conduite de base, des annonciateurs, des systèmes packagés et des systèmes instrumentés de sécurité. Elle s'applique aux procédés continus, batch et discontinus.
- **Apport principal** : le cycle de vie de la gestion des alarmes (§5.2), la rationalisation, la philosophie d'alarme et les indicateurs de performance.
- **Où l'obtenir** : IEC Webstore (prix en CHF), ou l'Association suisse de normalisation (SNV).

### ANSI/ISA-18.2 · Management of Alarm Systems for the Process Industries

- **Édition de référence** : 2016. Première édition en 2009.
- **Relation avec IEC 62682** : la norme internationale a été construite à partir d'ISA-18.2. Le contenu et le cycle de vie sont très proches.
- **Apport principal** : un tableau d'indicateurs de performance avec des valeurs de référence, largement repris par l'industrie et par les éditeurs de logiciels. Ce sont ces valeurs qu'utilise le calculateur.
- **Rapports techniques associés** (série ISA-TR18.2.x) : notamment la surveillance, l'évaluation et l'audit des systèmes d'alarmes (TR18.2.5) et les alarmes des procédés batch et discontinus (TR18.2.6).

### EEMUA 191 · Alarm systems: a guide to design, management and procurement

- **Édition en vigueur** : 4e édition, publiée fin 2024. Éditions précédentes : 1999, 2007, 2013.
- **Nature** : un **guide de bonnes pratiques**, pas une norme. Il ne contient pas d'exigences obligatoires : on ne peut pas s'en déclarer « conforme ». Il est néanmoins reconnu comme référence par plusieurs autorités de contrôle.
- **Apport principal** : la prise en compte des capacités cognitives de l'opérateur, qui sont limitées. Les normes ISA-18.2 et IEC 62682 sont alignées sur ses principes. La 4e édition harmonise sa terminologie avec ces normes et ajoute un volet sur les sites distants.
- **Ressource gratuite** : EEMUA propose une checklist pour le document de philosophie d'alarme.

## Référentiels connexes

| Référence | Sujet | Lien avec ce guide |
|---|---|---|
| NAMUR NA 102 | Recommandation de l'industrie des procédés germanophone sur la gestion des alarmes | Utile sur les sites chimiques et pharmaceutiques qui appliquent déjà les recommandations NAMUR |
| Série IEC 62443 | Sécurité des systèmes d'automatisation et de commande industriels | Intégrité des alarmes, contrôle d'accès, journalisation (voir [05](../methodology/05-mise-en-oeuvre-suivi.md)) |
| IEC 61511 | Systèmes instrumentés de sécurité pour les industries de transformation | Hors périmètre : les fonctions de sécurité ont leur propre cycle de vie |
| Série EN 54 | Systèmes de détection et d'alarme incendie | Hors périmètre réglementaire ; les principes de pertinence et de charge s'appliquent aux reports d'alarmes |
| Série EN 50131 | Systèmes d'alarme intrusion et hold-up | Idem |

## Correspondance entre ce guide et le cycle de vie

| Étape du guide | Étapes du cycle de vie (IEC 62682 / ISA-18.2) | Fichiers |
|---|---|---|
| 00 · Diagnostic | Audit (version allégée) | [00-diagnostic-rapide.md](../methodology/00-diagnostic-rapide.md) |
| 01 · Cadrage | Philosophie, identification | [01](../methodology/01-cadrage-philosophie.md), [philosophie-alarmes-modele.md](../templates/philosophie-alarmes-modele.md) |
| 02 · Collecte | Surveillance et évaluation (données) | [02](../methodology/02-collecte-journal.md), [inventaire-equipements.csv](../templates/inventaire-equipements.csv) |
| 03 · Mesure | Surveillance et évaluation | [03](../methodology/03-mesure-indicateurs.md), [calculateur](../tools/calcul-indicateurs-alarmes.xlsx) |
| 04 · Rationalisation | Rationalisation, conception détaillée | [04](../methodology/04-rationalisation.md), [base-alarmes-maitre.csv](../templates/base-alarmes-maitre.csv), [matrice-priorite.md](../templates/matrice-priorite.md) |
| 05 · Mise en œuvre et suivi | Mise en œuvre, exploitation, maintenance, gestion des modifications, audit | [05](../methodology/05-mise-en-oeuvre-suivi.md), [fiche-reflexe-operateur.md](../templates/fiche-reflexe-operateur.md) |

## Glossaire français · anglais

| Terme utilisé ici | Terme anglais courant | Sens |
|---|---|---|
| Avalanche d'alarmes | Alarm flood | Plus d'alarmes que l'opérateur ne peut en traiter (référence : plus de 10 en 10 minutes) |
| Alarme intermittente | Chattering alarm | Alarme qui s'active et revient à la normale de façon répétée en peu de temps |
| Alarme fugitive | Fleeting alarm | Alarme qui revient à la normale avant que l'opérateur puisse agir |
| Alarme figée | Stale alarm | Alarme active depuis très longtemps (référence : plus de 24 heures) |
| Alarme perturbatrice | Bad actor, nuisance alarm | Alarme qui génère une charge disproportionnée ou inutile |
| Registre des alarmes | Master alarm database | Liste documentée de toutes les alarmes avec leur justification et leurs réglages |
| Philosophie d'alarme | Alarm philosophy | Document qui fixe les règles de gestion des alarmes du site |
| Délai de réponse admissible | Allowable response time | Temps disponible pour agir avant que la conséquence se produise |
| Bande morte | Deadband | Écart nécessaire pour que l'alarme revienne à la normale |
| Temporisation à l'apparition | On-delay | Durée pendant laquelle la condition doit persister avant l'alarme |
| Mise en attente temporaire | Shelving | Retrait temporaire et tracé d'une alarme par l'opérateur |
| Suppression par conception | Suppressed by design | Inhibition automatique dans un état défini |
| Mise hors service | Out of service | Désactivation, en général pour maintenance |
| Première alarme | First-out | L'alarme qui signale la cause d'une séquence |

## Sources consultées pour les éditions

- IEC Webstore, fiche IEC 62682:2022 : https://webstore.iec.ch/publication/65543
- EEMUA, Publication 191 : https://eemua.org/products/publications/print/eemua-publication-191
- EEMUA, sommaire de la 4e édition (2024) : https://eemua.org/getattachment/9d3f8071-55c3-49bf-a74a-3bf6ad4a2e0f/Contents-EEMUA-Publication-191-Edition4-November-2024.pdf

*Éditions vérifiées en octobre 2026. Les normes évoluent : vérifiez l'édition en vigueur avant de vous y référer dans un document contractuel.*
