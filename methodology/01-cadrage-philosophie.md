# 01 · Cadrage et philosophie d'alarme

## Ce qu'est une alarme

Une alarme est un signal qui annonce à l'opérateur un dysfonctionnement, une dérive ou une situation anormale **qui exige de sa part une réponse dans un délai donné**. C'est l'idée commune aux trois référentiels (IEC 62682, ISA-18.2, EEMUA 191).

Tout le reste de la démarche découle de cette définition. Avant de garder une alarme, posez trois questions :

1. **Est-ce anormal ?** Une machine à l'arrêt en fin de poste ou une température basse en début de nettoyage ne le sont pas.
2. **L'opérateur doit-il faire quelque chose ?** Si la réponse est « rien » ou « il le sait déjà », ce n'est pas une alarme.
3. **Y a-t-il un délai ?** Si l'action peut attendre la tournée de demain, un ordre de maintenance ou un rapport suffit.

Trois oui : c'est une alarme. Un seul non : c'est un **événement**, un **message**, une **information de rapport** ou un **ordre de maintenance**. Ces informations restent utiles, mais elles ne doivent pas solliciter l'opérateur comme une alarme.

## Le cycle de vie

IEC 62682 et ISA-18.2 décrivent la gestion des alarmes comme un cycle en dix étapes (IEC 62682:2022, §5.2). En pratique, dans une PME :

| Étape | Ce qu'elle signifie pour une PME |
|---|---|
| Philosophie | Un document court qui fixe les règles : ce qu'est une alarme, les priorités, qui décide. |
| Identification | D'où viennent les alarmes : analyses de risques, exigences qualité, retours d'incidents. |
| Rationalisation | La revue alarme par alarme. C'est le cœur du travail. |
| Conception détaillée | Seuils, bandes mortes, temporisations, textes, affichage. |
| Mise en œuvre | Modification des automates et de la supervision, essais, formation. |
| Exploitation | Les opérateurs utilisent le système, avec des fiches réflexes. |
| Maintenance | Tests des capteurs, réparation des alarmes défaillantes. |
| Surveillance et évaluation | Mesure régulière des indicateurs. |
| Gestion des modifications | Toute modification passe par une procédure tracée. |
| Audit | Revue périodique de l'ensemble. |

Les normes prévoient plusieurs **points d'entrée** dans le cycle. Pour une installation existante, le plus efficace est presque toujours d'entrer par la **surveillance** (mesurer), puis de **rationaliser** les pires alarmes. La philosophie se rédige ensuite, à partir des décisions prises en atelier. Un document de philosophie écrit avant d'avoir regardé les données reste en général dans un classeur.

## La philosophie d'alarme

C'est le document de référence du site. Il tient en quelques pages et répond à ces questions :

- quel est le périmètre (quels postes, quels systèmes) ;
- quelle est la définition d'une alarme sur le site ;
- quels sont les niveaux de priorité et comment on les attribue (matrice) ;
- quelles règles de conception s'appliquent (seuils, bandes mortes, temporisations, textes) ;
- comment l'IHM présente les alarmes (couleurs, sons, regroupements) ;
- comment on inhibe une alarme temporairement, et qui l'autorise ;
- quels indicateurs on suit, avec quelles cibles ;
- qui est responsable de quoi ;
- comment on modifie une alarme ;
- comment on forme les opérateurs.

Trame prête à remplir : [philosophie-alarmes-modele.md](../templates/philosophie-alarmes-modele.md).

## Cadrer une démarche dans une PME

### Périmètre

Un poste opérateur et un système à la fois. Si la supervision couvre plusieurs ateliers avec un seul opérateur, c'est **un** poste. Si deux opérateurs se partagent les écrans par zone, ce sont **deux** postes, à analyser séparément.

N'oubliez pas les **systèmes packagés** : chaudière, compresseurs, groupes froid, stations de traitement. Ils ont souvent leurs propres écrans et leurs propres alarmes, qui ne remontent qu'en partie dans la supervision. L'opérateur, lui, les subit toutes.

### Qui doit participer

| Rôle | Pourquoi |
|---|---|
| Un opérateur expérimenté | Il sait quelles alarmes il ignore et pourquoi. Sans lui, la rationalisation est théorique. |
| Le responsable maintenance | Il connaît les capteurs défaillants et les réglages bricolés. |
| L'automaticien ou l'intégrateur | Il sait ce qui est modifiable, à quel coût. |
| Qualité, sécurité, environnement | Ils valident les conséquences et les priorités des alarmes qui les concernent. |
| Un animateur | Il tient la méthode, le rythme et la trace écrite. Idéalement extérieur à l'équipe. |

### Déroulé type

| Phase | Durée indicative | Livrable |
|---|---|---|
| Diagnostic : collecte et mesure | 1 à 2 jours | Indicateurs, top 10, pires périodes, alarmes figées |
| Atelier de rationalisation du top 10 | 1 à 2 demi-journées | Registre des alarmes traitées, plan d'action |
| Mise en œuvre | selon l'intégrateur | Modifications tracées, fiches réflexes |
| Mesure de contrôle | 1 jour, 4 à 6 semaines après | Indicateurs avant et après |

### Ce qu'il faut demander avant de commencer

- un export du journal d'alarmes sur deux à quatre semaines (voir [02 · Collecte](02-collecte-journal.md)) ;
- la liste des alarmes configurées, si elle existe ;
- la liste des inhibitions en cours ;
- les analyses de risques existantes, si des alarmes y sont créditées comme barrière ;
- le contact de l'intégrateur et l'état de la documentation des automates.

## Une précaution importante

Certaines alarmes sont créditées comme **barrière de protection** dans une analyse de risques (HAZOP, LOPA ou équivalent). Elles ont des exigences propres : temps de réponse démontré, tests périodiques, formation spécifique. Ne supprimez, ne retardez ni ne déclassez jamais une telle alarme sans l'accord du propriétaire de l'analyse de risques.
