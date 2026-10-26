# 03 · Mesure des indicateurs

Mesurer avant de modifier. Les indicateurs disent **où regarder** ; ils ne disent pas quoi changer. C'est le rôle de la [rationalisation](04-rationalisation.md).

## Utiliser le calculateur

1. Ouvrez [calcul-indicateurs-alarmes.xlsx](../tools/calcul-indicateurs-alarmes.xlsx). Il contient le journal fictif de l'exemple : les indicateurs sont déjà calculés.
2. Onglet **Journal** : effacez les colonnes A à F, collez votre journal à partir de la ligne 2. Ne touchez pas aux colonnes G à U.
3. Onglet **Paramètres** : nombre de postes opérateur, libellés de vos priorités. Laissez les dates vides pour que la période soit déduite du journal.
4. Lisez **Indicateurs**, **Top 10** et **Pires périodes**.

Le classeur ne contient ni macro ni connexion externe. Il est préparé pour 10 000 alarmes ; au-delà, recopiez vers le bas la dernière ligne des colonnes G à U.

## Les indicateurs et leurs valeurs de référence

Valeurs de référence telles que publiées pour ISA-18.2 et IEC 62682, et convergentes avec EEMUA 191. Elles s'entendent **par poste opérateur** et en **fonctionnement normal**. Votre philosophie d'alarme peut fixer d'autres cibles.

| Indicateur | Référence | Ce qu'un écart signifie |
|---|---|---|
| Alarmes par jour et par poste | env. 150 acceptable, env. 300 maximum gérable | Au-delà de 300, l'opérateur ne peut plus traiter chaque alarme avec attention. |
| Alarmes par heure | env. 6 acceptable, env. 12 maximum gérable | Même lecture, à l'échelle de l'heure. |
| Alarmes par 10 minutes | env. 1 | C'est la cible de régime établi de EEMUA 191. |
| Maximum en 10 minutes | 10 ou moins | Au-delà : avalanche. L'opérateur trie, il ne traite plus. |
| Temps en avalanche | moins de 1 % | Une avalanche a presque toujours une cause unique identifiable. |
| Heures avec plus de 30 alarmes | moins de 1 % | Révèle les heures saturées que la moyenne masque. |
| Part du top 10 | 1 à 5 % au maximum | Une valeur élevée est une bonne nouvelle : quelques corrections suffiront. |
| Alarmes intermittentes (chattering) | aucune | Réglage absent : bande morte ou temporisation. |
| Alarmes fugitives (fleeting) | aucune | Retour à la normale trop rapide pour qu'une action soit possible. |
| Alarmes figées (stale) | moins de 5 par jour, avec plan d'action | Capteur défaillant, alarme mal définie, ou situation acceptée par habitude. |
| Répartition des priorités | env. 80 % basse, 15 % moyenne, 5 % haute | Si tout est prioritaire, plus rien ne l'est. |
| Inhibitions et modifications non autorisées | aucune | Problème de gestion des modifications, et de sécurité. |

## Définitions retenues dans le calculateur

- **Fenêtres fixes.** Les fenêtres de 10 minutes et d'une heure sont alignées sur le début de la période. Les normes décrivent une avalanche par un début (plus de 10 alarmes en 10 minutes) et une fin (retour sous 5 alarmes en 10 minutes). Les fenêtres fixes donnent un résultat proche, plus simple à vérifier à la main, mais une avalanche à cheval sur deux fenêtres apparaît coupée en deux.
- **Intermittente** : au moins 3 activations du même tag en 60 secondes.
- **Fugitive** : retour à la normale en moins de 5 secondes.
- **Figée** : active plus de 24 heures, ou toujours active plus de 24 heures avant la fin de la période.

Tous ces seuils sont réglables dans l'onglet Paramètres.

## Lire les résultats

### 1. Regarder la structure, pas seulement la moyenne

Une moyenne de 190 alarmes par jour peut sembler presque acceptable. Si 87 % de ces alarmes viennent de dix tags, si un tiers vient d'une seule chambre froide qui oscille, et si les pires 10 minutes en contiennent 44, le système n'est pas « presque acceptable » : il est déséquilibré. C'est exactement le cas de l'[exemple](../examples/analyse-site-fictif.md).

### 2. Commencer par le top 10

Le top 10 concentre le gain. Pour chaque ligne, les colonnes Intermittente, Fugitive et Figée orientent déjà le traitement :

| Constat | Piste probable |
|---|---|
| Intermittente ou fugitive | Réglage : bande morte, temporisation à l'apparition |
| Figée | Capteur défaillant, alarme sans objet, ou protection aveugle (à traiter en urgence) |
| Ni l'un ni l'autre, mais très fréquente | État normal présenté comme une alarme, ou seuil mal placé |

### 3. Lire les avalanches par leur première alarme

Dans l'onglet Pires périodes, la première alarme d'une fenêtre est souvent la **cause** et les suivantes les **conséquences**. Si la cause est dans la fenêtre précédente, regardez-la aussi. Une avalanche se traite rarement alarme par alarme : on traite la cause (suppression des conséquences tant que la cause est active, regroupement, alarme de synthèse).

### 4. Traiter les alarmes figées comme des signaux, pas comme du bruit

Une alarme figée sur un capteur de protection (niveau très haut, pression haute) signifie souvent que **la protection ne fonctionne plus**. C'est le constat le plus important d'un diagnostic, même s'il ne pèse rien dans les statistiques.

## Pièges de lecture

- **Petit système.** Sur une installation de quelques dizaines de tags, la part du top 10 reste élevée par construction. Regardez plutôt son volume absolu.
- **Plusieurs postes.** Le calculateur divise les moyennes par le nombre de postes, en supposant une charge égale. Si un poste porte l'essentiel, faites un fichier par poste.
- **Un journal calme n'est pas forcément un bon signe.** Vérifiez la liste des inhibitions et des alarmes mises hors service.
- **Une semaine atypique fausse tout.** Notez les arrêts, travaux et incidents de la période, et comparez avec une deuxième semaine si possible.
- **Les chiffres ne disent pas si une alarme est utile.** Une alarme rare peut être inutile ; une alarme fréquente peut être légitime. C'est l'atelier de rationalisation qui tranche.
