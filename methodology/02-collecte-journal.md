# 02 · Collecte du journal et inventaire

Sans journal d'alarmes, on discute d'impressions. Avec un journal, on discute de faits. Cette étape conditionne la qualité de tout le reste.

## Où trouver le journal

| Source | Ce qu'on y trouve | Point d'attention |
|---|---|---|
| Historique d'alarmes de la supervision (SCADA) | Le journal le plus complet en général | Vérifier la durée de rétention, parfois quelques jours seulement |
| Gestion technique centralisée (GTC, GTB) | Alarmes des utilités et des bâtiments | Mélange fréquent d'alarmes et d'événements |
| IHM locales d'automates | Alarmes d'une machine ou d'une ligne | Export souvent limité, parfois sur clé USB uniquement |
| Systèmes packagés (chaudière, compresseurs, froid) | Alarmes propres à l'équipement | Ne remontent souvent qu'en partie ; à inventorier |

Le journal utile est celui de ce que **l'opérateur voit réellement**. Si les alarmes d'un système packagé s'affichent sur un écran local à côté du poste, elles font partie de sa charge, même si la supervision ne les enregistre pas.

## Quelle période

- **Deux à quatre semaines** d'exploitation normale. Une semaine suffit pour un premier diagnostic.
- Notez les **événements particuliers** de la période : arrêts programmés, incidents, travaux, jours fériés. Ils expliquent les pics.
- Évitez les périodes d'arrêt annuel ou de démarrage après travaux, sauf si c'est précisément ce que vous voulez analyser.

## Le format attendu par le calculateur

Une ligne par alarme, c'est-à-dire par **occurrence** :

| Colonne | Contenu | Exemple |
|---|---|---|
| horodatage_activation | Date et heure d'apparition | 2026-03-04 10:47:12 |
| horodatage_retour | Date et heure de retour à la normale, vide si encore active | 2026-03-04 11:27:12 |
| tag | Identifiant unique du point | CHD_TRIP |
| description | Texte affiché à l'opérateur | Chaudière vapeur - déclenchement brûleur |
| priorite | Priorité configurée | Haute |
| zone | Zone, atelier ou système | Utilités |

## Transformer un journal à événements

Beaucoup de systèmes exportent un journal **à événements** : une ligne pour l'apparition, une pour l'acquittement, une pour le retour à la normale. Il faut regrouper ces lignes en occurrences.

Méthode dans Excel :

1. Gardez uniquement les lignes d'apparition et de retour. Les acquittements sont utiles pour d'autres analyses (temps de réaction), pas pour la charge.
2. Triez par **tag**, puis par **date et heure**.
3. Pour chaque ligne d'apparition, l'horodatage de retour est celui de la **ligne de retour suivante du même tag**. Une formule du type `SI(ET(tag suivant = tag ; type suivant = "retour") ; date suivante ; "")` suffit dans la plupart des cas.
4. Supprimez les lignes de retour, puis retriez par date et heure.
5. Contrôlez quelques tags à la main avant de lancer le calcul.

Si l'export est volumineux ou récurrent, Power Query (intégré à Excel) automatise ces étapes.

## Les pièges classiques

- **Horloges non synchronisées.** Si les automates et la supervision ne sont pas à la même heure, les séquences d'avalanche deviennent illisibles. Vérifiez la synchronisation (NTP) avant toute analyse fine.
- **Changement d'heure.** En Suisse, le dernier dimanche d'octobre, l'heure de 2 h à 3 h existe deux fois. Exportez en temps universel (UTC) si le système le permet, ou excluez cette nuit-là.
- **Événements mélangés aux alarmes.** Changements d'état, connexions d'utilisateurs, messages système : filtrez-les par type ou par priorité.
- **Doublons multi-postes.** Une même alarme peut apparaître sur plusieurs postes et être enregistrée plusieurs fois. Dédoublonnez par tag et horodatage.
- **Alarmes inhibées.** Elles n'apparaissent pas dans le journal. Un journal calme peut cacher un système où tout est inhibé. Demandez toujours la liste des inhibitions en cours.
- **Rétention trop courte.** Certains systèmes écrasent leur historique après quelques jours. Planifiez l'export en conséquence.

## Inventaire des équipements

En parallèle du journal, dressez l'inventaire de ce qui est installé et de ce qui remonte réellement en supervision. C'est souvent là qu'on découvre les angles morts : un groupe froid dont seul le défaut général remonte, une centrale de détection reliée par un unique contact sec, un automate dont personne n'a le programme.

Modèle : [inventaire-equipements.csv](../templates/inventaire-equipements.csv). Pour un site peu documenté, suivez la [checklist de prise en main](../templates/checklist-prise-en-main-site.md).

## Confidentialité

Un journal d'alarmes révèle l'architecture du site, ses équipements, ses faiblesses et ses horaires. Traitez-le comme une donnée sensible :

- analyse sur site ou sur un poste maîtrisé, hors ligne ;
- anonymisation des tags et des descriptions avant tout partage externe ;
- aucun dépôt sur un service en ligne sans accord écrit du site ;
- suppression des copies à la fin de la mission.
