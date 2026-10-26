# alarm-rationalization-field-guide

**Guide de terrain et outils libres pour rationaliser les alarmes des supervisions industrielles. Pensé pour les PME.**

Méthode en cinq étapes, modèles prêts à remplir, calculateur Excel des indicateurs de charge et un site fictif analysé de bout en bout. Fondé sur IEC 62682, ISA-18.2 et EEMUA 191, traduit en pratique de terrain.

---

## Le problème

Dans une PME industrielle, les alarmes s'accumulent au fil des projets. Chaque intégrateur ajoute les siennes, chaque modification en crée de nouvelles, et presque personne n'en supprime. Le résultat est connu de tous les exploitants : des centaines d'alarmes par jour, des états normaux affichés comme des anomalies, des alarmes qui clignotent en boucle et d'autres qui restent rouges depuis des semaines.

L'opérateur s'adapte. Il apprend à acquitter sans lire. Le jour où une alarme compte vraiment, elle arrive au milieu de quarante autres.

Les normes qui traitent ce problème existent depuis longtemps. Elles ont été écrites pour la chimie, le pétrole et l'énergie, avec des équipes dédiées et des budgets d'ingénierie conséquents. Ce guide en reprend les principes et les rend applicables par une équipe de maintenance de cinq personnes, avec Excel et deux jours d'atelier.

## Commencer en 15 minutes

1. **Répondez au [diagnostic rapide](methodology/00-diagnostic-rapide.md).** Vingt questions en oui ou non, et vous saurez où vous en êtes.
2. **Exportez une semaine de journal d'alarmes** et collez-la dans le [calculateur](tools/calcul-indicateurs-alarmes.xlsx). Il compare votre charge aux valeurs de référence publiées.
3. **Regardez votre top 10.** Dans la plupart des installations, dix alarmes produisent l'essentiel du bruit. C'est le gain le plus rapide.

## Ce que montre l'exemple

Le dossier [`examples/`](examples/) analyse une semaine d'alarmes d'une laiterie imaginaire, LactoDémo SA. Toutes les données sont fictives, mais les situations sont celles qu'on rencontre sur le terrain.

| Constat | Valeur | Référence |
|---|---|---|
| Alarmes par jour et par poste | 191 | env. 150 acceptable, 300 maximum gérable |
| Part des activations due aux 10 alarmes les plus fréquentes | 87 % | 1 à 5 % |
| Pire fenêtre de 10 minutes | 44 alarmes | 10 au maximum |
| Alarmes en priorité haute | 36 % | env. 5 % |
| Détecteur de niveau très haut bloqué toute la semaine | 1 | aucun |

La moyenne journalière paraît presque acceptable. La structure, elle, ne l'est pas : un seul point de mesure mal réglé produit un tiers de la charge, et le capteur bloqué rend aveugle une protection contre le débordement. Le plan proposé, deux réparations urgentes et sept modifications de configuration, réduit la charge estimée de 84 % sans toucher au procédé. Détails dans [l'analyse](examples/analyse-site-fictif.md).

## Contenu

| Dossier | Fichier | Rôle |
|---|---|---|
| `methodology/` | [00-diagnostic-rapide.md](methodology/00-diagnostic-rapide.md) | Auto-évaluation en 20 questions |
| | [01-cadrage-philosophie.md](methodology/01-cadrage-philosophie.md) | Ce qu'est une alarme, cycle de vie, cadrage d'une démarche en PME |
| | [02-collecte-journal.md](methodology/02-collecte-journal.md) | Obtenir un journal exploitable et inventorier les équipements |
| | [03-mesure-indicateurs.md](methodology/03-mesure-indicateurs.md) | Indicateurs, valeurs de référence, pièges de lecture |
| | [04-rationalisation.md](methodology/04-rationalisation.md) | Revue alarme par alarme, matrice de priorité, traitements types |
| | [05-mise-en-oeuvre-suivi.md](methodology/05-mise-en-oeuvre-suivi.md) | Modifications, transfert aux opérateurs, suivi dans la durée |
| `templates/` | [base-alarmes-maitre.csv](templates/base-alarmes-maitre.csv) | Registre des alarmes rationalisées (une ligne par alarme) |
| | [inventaire-equipements.csv](templates/inventaire-equipements.csv) | Ce qui est installé et ce qui remonte réellement en supervision |
| | [matrice-priorite.md](templates/matrice-priorite.md) | Priorité selon la gravité et le délai de réponse |
| | [philosophie-alarmes-modele.md](templates/philosophie-alarmes-modele.md) | Trame du document de philosophie d'alarme |
| | [fiche-reflexe-operateur.md](templates/fiche-reflexe-operateur.md) | Une alarme, une page : que faire et en combien de temps |
| | [checklist-prise-en-main-site.md](templates/checklist-prise-en-main-site.md) | Aborder un site peu ou pas documenté |
| | [notification-intervention-tiers.md](templates/notification-intervention-tiers.md) | Prévenir l'exploitation avant des travaux qui touchent aux alarmes |
| `tools/` | [calcul-indicateurs-alarmes.xlsx](tools/calcul-indicateurs-alarmes.xlsx) | Calculateur : journal collé, indicateurs, top 10, pires périodes |
| `standards/` | [references.md](standards/references.md) | Normes et guides de référence, résumés et correspondances |
| `examples/` | [site-fictif-lactodemo.md](examples/site-fictif-lactodemo.md) | Description du site fictif |
| | [journal-alarmes-fictif.csv](examples/journal-alarmes-fictif.csv) | Journal synthétique de 7 jours, 1 336 alarmes |
| | [analyse-site-fictif.md](examples/analyse-site-fictif.md) | Analyse complète et plan d'action |

## La méthode en une page

1. **Cadrer.** Un poste opérateur, un système, une équipe. Définir ce qu'est une alarme chez vous.
2. **Collecter.** Un journal d'alarmes de deux à quatre semaines et l'inventaire de ce qui est installé.
3. **Mesurer.** Charge moyenne, avalanches, top 10, alarmes intermittentes, figées et fugitives, répartition des priorités.
4. **Rationaliser.** Pour chaque alarme du top 10 et chaque alarme figée ou intermittente : cause, conséquence, action attendue, délai, priorité, réglage. Documenter dans le registre.
5. **Mettre en œuvre et suivre.** Modifications tracées, fiches réflexes pour les opérateurs, indicateurs revus chaque mois.

On commence par mesurer, pas par rédiger un document de quarante pages. La philosophie d'alarme se construit à partir des premières décisions concrètes.

## À qui s'adresse ce guide

Aux responsables de maintenance, de production et d'automatisme de PME industrielles : agroalimentaire, pharma, chimie fine, traitement des eaux, utilités et bâtiments techniques. Aux intégrateurs qui livrent des supervisions. À tout exploitant qui se demande pourquoi ses opérateurs n'écoutent plus les alarmes.

## Ce que ce guide n'est pas

- **Pas un substitut aux normes.** IEC 62682, ISA-18.2 et EEMUA 191 sont des documents payants. Ce guide en résume les principes avec ses propres mots et renvoie à l'édition officielle pour toute exigence précise.
- **Pas une méthode pour les systèmes instrumentés de sécurité.** Une alarme créditée comme barrière dans une analyse de risques ne se modifie pas sans le propriétaire de cette analyse. Les systèmes réglementés (détection incendie, intrusion) ont leur propre cadre normatif, même si les principes de ce guide s'y appliquent.
- **Pas un outil qui décide à votre place.** Le calculateur mesure. La rationalisation reste une décision humaine, documentée et validée par l'exploitation.

## Confidentialité

Un journal d'alarmes décrit l'architecture d'un site, ses points faibles et ses habitudes d'exploitation. C'est une donnée sensible, y compris du point de vue de la cybersécurité OT. Le calculateur fonctionne hors ligne, sans macro ni connexion. Analysez sur site, anonymisez les tags avant tout partage externe et ne déposez pas de journal brut sur un service en ligne sans accord formel.

## Retours et contributions

Les retours de terrain sont bienvenus : une situation que le guide ne couvre pas, un indicateur mal défini, un modèle à améliorer. Ouvrez une *issue* ou proposez une modification.

## Auteur

**Julien Sisavath** : quinze ans de terrain industriel dans le ferroviaire et la pharma, sécurité des systèmes industriels (OT/ICS). Basé en Suisse romande.

Besoin d'un regard externe sur votre système d'alarmes ? [juliensisavath.com](https://juliensisavath.com)

## Licence

Contenu publié sous licence [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE.md). Vous pouvez l'utiliser, l'adapter et le diffuser, y compris à des fins commerciales, en citant la source.

---

### English summary

A practical field guide and free toolkit for alarm rationalization in small and mid-sized industrial sites, grounded in IEC 62682, ISA-18.2 and EEMUA 191. It includes a five-step method, ready-to-use templates (master alarm database, priority matrix, alarm philosophy outline, operator response cards), an Excel calculator that benchmarks an alarm log against published performance targets, and a fully synthetic worked example. Content is in French.
