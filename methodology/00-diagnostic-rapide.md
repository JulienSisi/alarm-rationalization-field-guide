# 00 · Diagnostic rapide

Vingt questions, une réponse par oui ou par non. Comptez un point par **oui**. Répondez sur ce que vous pouvez montrer, pas sur ce que vous pensez : « je crois que oui » vaut non.

Durée : 10 minutes. Idéalement, faites-le remplir séparément par un opérateur et par le responsable maintenance, puis comparez.

---

## A. Charge de l'opérateur

| # | Question | Oui / Non |
|---|---|---|
| 1 | Connaissez-vous le nombre d'alarmes qu'un opérateur reçoit par jour, mesuré à partir du journal et non estimé ? | |
| 2 | Ce nombre est-il inférieur à environ 150 par poste opérateur et par jour, en fonctionnement normal ? | |
| 3 | Un incident courant (déclenchement de chaudière, coupure réseau, arrêt d'une ligne) produit-il moins de 10 alarmes dans les 10 premières minutes ? | |
| 4 | Aucune alarme ne reste-t-elle active plus de 24 heures sans plan d'action identifié ? | |
| 5 | Aucune alarme ne réapparaît-elle plusieurs fois par minute ? | |

## B. Pertinence des alarmes

| # | Question | Oui / Non |
|---|---|---|
| 6 | Chaque alarme correspond-elle à une action précise que l'opérateur doit effectuer ? | |
| 7 | Les états normaux (machine à l'arrêt, phase de nettoyage, équipement en maintenance) ne déclenchent-ils aucune alarme ? | |
| 8 | La majorité des alarmes est-elle en priorité basse, et seule une petite minorité en priorité haute ? | |
| 9 | Un opérateur récemment formé sait-il, pour les dix alarmes les plus fréquentes, quoi faire et en combien de temps ? | |
| 10 | Les défauts d'instrumentation et de communication sont-ils présentés séparément des alarmes de procédé ? | |

## C. Organisation et documentation

| # | Question | Oui / Non |
|---|---|---|
| 11 | Existe-t-il un document écrit qui définit ce qu'est une alarme sur votre site (philosophie d'alarme) ? | |
| 12 | Existe-t-il une liste à jour de toutes les alarmes avec leur seuil, leur priorité et leur justification ? | |
| 13 | Une personne est-elle nommément responsable du système d'alarmes ? | |
| 14 | Les indicateurs de charge d'alarmes sont-ils revus au moins une fois par mois ? | |
| 15 | Un opérateur peut-il signaler une alarme inutile et obtenir une réponse dans un délai connu ? | |

## D. Modifications et sécurité

| # | Question | Oui / Non |
|---|---|---|
| 16 | Toute modification de seuil, de priorité ou toute inhibition passe-t-elle par une procédure de modification tracée ? | |
| 17 | Les inhibitions temporaires ont-elles une durée limitée et figurent-elles sur une liste consultable ? | |
| 18 | Les accès qui permettent de modifier les alarmes sont-ils nominatifs et protégés ? | |
| 19 | Les capteurs liés aux alarmes importantes sont-ils testés périodiquement ? | |
| 20 | Le journal d'alarmes est-il conservé au moins trois mois, avec des horloges synchronisées ? | |

**Total : ____ / 20**

---

## Lecture du score

| Score | Lecture |
|---|---|
| 16 à 20 | Système maîtrisé. Restez sur un suivi mensuel des indicateurs et un audit annuel. |
| 10 à 15 | Système fragile. Il fonctionne grâce à l'expérience des opérateurs en place. Mesurez la charge réelle et traitez le top 10. |
| 0 à 9 | Le système d'alarmes génère du risque au lieu d'en réduire. Une démarche structurée est justifiée : mesure, rationalisation, philosophie d'alarme. |

## Signaux d'alerte immédiats

Indépendamment du score, chacune de ces situations justifie une action **cette semaine** :

- une alarme liée à une protection (niveau très haut, pression haute, température critique) est figée depuis plusieurs jours ;
- les opérateurs acquittent les alarmes en bloc, sans les lire ;
- des alarmes sont inhibées sans que personne sache depuis quand ni pourquoi ;
- personne ne peut dire qui a le droit de modifier un seuil ;
- une alarme importante a déjà été manquée parce qu'elle était noyée dans d'autres.

## Étape suivante

Les questions 1 à 5 se vérifient en une heure avec le [calculateur](../tools/calcul-indicateurs-alarmes.xlsx). Voir [02 · Collecte du journal](02-collecte-journal.md) puis [03 · Mesure](03-mesure-indicateurs.md).

*Les seuils cités (150 alarmes par jour, 10 alarmes en 10 minutes, 24 heures) sont les valeurs de référence publiées pour ISA-18.2, IEC 62682 et EEMUA 191. Voir [references.md](../standards/references.md).*
