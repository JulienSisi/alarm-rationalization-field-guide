# Site fictif · LactoDémo SA

> **Entièrement fictif.** LactoDémo SA n'existe pas. Le site, les équipements, les tags et le journal d'alarmes ont été construits pour illustrer la méthode. Toute ressemblance avec une installation réelle serait fortuite.

## Le site

Laiterie industrielle de taille moyenne : environ 60 collaborateurs, réception de lait cru, pasteurisation, conditionnement et stockage au froid. Une station de prétraitement des eaux usées (STEP) avant rejet au réseau communal.

- **Production** : du lundi au samedi, de 5 h à 22 h.
- **Nettoyage en place (NEP)** : trois cycles par jour de production, un le dimanche.
- **Conduite** : **un seul poste opérateur** en salle de contrôle, qui supervise tout le site.

## Les systèmes

| Zone | Équipements principaux | Remontée en supervision |
|---|---|---|
| Réception | Pompe de dépotage, tanks de lait cru 1 à 3, débitmètre | Automate 1 |
| Pasteurisation | Pasteurisateur à plaques, vanne de dérivation, chambrage | Automate 2 |
| NEP | Cuves soude et acide, pompes, échangeur | Automate 3 |
| Conditionnement | Conditionneuses 1, 2 et 4, ventilation de la salle | Automates 4 et 5 |
| Froid | Chambres froides 1 et 2, groupes froid, eau glacée | Contacts secs et Modbus |
| Utilités | Chaudière vapeur (packagée), compresseurs d'air, onduleur | Contacts secs |
| STEP | Bassin tampon, neutralisation, mesure de pH | Automate 5 |

La supervision a été installée il y a une dizaine d'années, puis complétée par trois intégrateurs successifs. Il n'existe ni liste d'alarmes à jour ni philosophie d'alarme. Les priorités ont été attribuées au cas par cas, à la création de chaque alarme.

## Ce que disent les opérateurs

- « La chambre froide 2 sonne tout le temps, on acquitte. »
- « Les arrêts des conditionneuses, on les voit déjà sur la ligne. »
- « Au début du NEP, il y a toujours des alarmes, c'est normal. »
- « Le niveau très haut du tank 3 est rouge depuis des jours, la maintenance est au courant. »

Chacune de ces phrases se retrouve dans les chiffres. La quatrième est la plus grave.

## La semaine analysée

Du lundi 2 mars 2026, 0 h, au lundi 9 mars 2026, 0 h. Deux incidents notables :

- **Mercredi 4 mars, 10 h 47** : déclenchement du brûleur de la chaudière vapeur. Perte de vapeur pour le pasteurisateur et le NEP pendant une quarantaine de minutes.
- **Samedi 7 mars, 6 h 02** : micro-coupure du réseau électrique. Pertes de communication avec les automates, arrêts des machines, défaut d'un compresseur du groupe froid.

## Les données

- [journal-alarmes-fictif.csv](journal-alarmes-fictif.csv) : 1 336 alarmes, 33 tags, une ligne par occurrence.
- Le même journal est pré-chargé dans le [calculateur](../tools/calcul-indicateurs-alarmes.xlsx).
- L'analyse complète : [analyse-site-fictif.md](analyse-site-fictif.md).
