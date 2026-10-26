# 05 · Mise en œuvre, transfert et suivi

Une rationalisation qui reste dans un tableau ne change rien pour l'opérateur. Et un système d'alarmes nettoyé se dégrade en dix-huit mois si personne ne le surveille.

## Mettre en œuvre les modifications

1. **Regrouper** les modifications par automate ou par système pour limiter les interventions.
2. **Passer chaque modification par la gestion des modifications du site** : demande écrite, analyse d'impact, validation, trace. Une modification de seuil est une modification.
3. **Tester** : déclencher l'alarme modifiée (simulation ou essai réel), vérifier le texte, la priorité, l'inhibition conditionnelle et le retour.
4. **Mettre à jour le registre** : statut « implémentée », date, référence de la modification.
5. **Prévenir les opérateurs avant**, pas après. Une alarme qui disparaît sans explication crée de la méfiance.

Pour les travaux confiés à un tiers (intégrateur, fournisseur, installateur), utilisez la [notification d'intervention](../templates/notification-intervention-tiers.md) : elle évite les avalanches imprévues pendant les travaux et les alarmes oubliées en inhibition après leur départ.

## Transférer aux opérateurs

L'objectif est qu'un opérateur récemment formé sache réagir correctement aux alarmes les plus fréquentes et les plus graves.

- **Une fiche réflexe par alarme importante** : cause probable, vérifications, action, délai, qui appeler. Une page au maximum. Modèle : [fiche-reflexe-operateur.md](../templates/fiche-reflexe-operateur.md).
- **Accès direct depuis l'IHM** quand c'est possible (lien ou numéro de fiche dans le texte de l'alarme), sinon un classeur au poste.
- **Courte session de formation** après chaque lot de modifications : ce qui a changé, pourquoi, ce qui reste à surveiller.
- **Retour des opérateurs** : un moyen simple de signaler une alarme inutile ou mal réglée, avec une réponse dans un délai connu.

## Suivre dans la durée

| Fréquence | Action | Qui |
|---|---|---|
| Chaque semaine, pendant 2 mois après les modifications | Top 10 et alarmes figées | Responsable du système d'alarmes |
| Chaque mois | Indicateurs complets avec le calculateur, comparaison au mois précédent | Responsable du système d'alarmes |
| Chaque trimestre | Revue des inhibitions en cours et des modifications de la période | Exploitation et maintenance |
| Chaque année | Audit : philosophie, registre, indicateurs, gestion des modifications, formation | Personne extérieure à l'équipe si possible |

Une règle simple tient le système propre : **toute nouvelle alarme passe par les questions de la rationalisation avant d'être créée**. Les intégrateurs doivent la connaître et la respecter.

## Le lien avec la cybersécurité OT

Le système d'alarmes est l'un des premiers moyens de détecter qu'une installation ne se comporte pas normalement, quelle qu'en soit la cause. Son intégrité compte donc aussi du point de vue de la sécurité informatique industrielle :

- une alarme inhibée sans trace, ou un seuil modifié sans autorisation, sont des événements de sécurité au même titre que des défauts d'exploitation ;
- les accès permettant de modifier les alarmes doivent être nominatifs et journalisés ;
- les pertes de communication entre automates et supervision méritent une analyse, pas seulement un acquittement ;
- les journaux d'alarmes eux-mêmes sont des données sensibles (voir [02 · Collecte](02-collecte-journal.md)).

La série IEC 62443 traite ces exigences (contrôle d'accès, journalisation, intégrité) pour les systèmes d'automatisation industriels. Une démarche de rationalisation est une bonne occasion de vérifier ces points.

## Signes que le système se dégrade

- le top 10 du mois contient des alarmes qui avaient été traitées ;
- la liste des inhibitions s'allonge ;
- de nouvelles alarmes apparaissent sans entrée dans le registre ;
- les opérateurs recommencent à acquitter en bloc.

Chacun de ces signes justifie une séance de rationalisation ciblée, pas un nouveau projet.
