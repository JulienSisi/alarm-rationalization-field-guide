# Checklist · Prise en main d'un site peu documenté

> À utiliser lors des premières visites d'un site dont les installations sont mal ou pas documentées. Objectif : savoir ce qui est installé, ce qui remonte réellement à l'opérateur, et où sont les angles morts. Cochez, notez, photographiez (avec autorisation).

## 1. Avant la visite

- [ ] Interlocuteurs identifiés : exploitation, maintenance, automatisme ou intégrateur, qualité, sécurité
- [ ] Règles d'accès et de sécurité du site connues (EPI, permis, zones interdites, photos autorisées ou non)
- [ ] Documentation existante demandée : plans, schémas, listes d'alarmes, contrats de maintenance
- [ ] Export du journal d'alarmes demandé (2 à 4 semaines) et liste des inhibitions en cours
- [ ] Accord écrit sur la confidentialité et le traitement des données

## 2. Le poste opérateur

- [ ] Nombre de postes et répartition des zones entre opérateurs
- [ ] Écrans présents au poste : supervision, IHM locales, écrans de systèmes packagés, report d'alarmes
- [ ] Alarmes sonores : combien de sons différents, d'où viennent-ils
- [ ] Ce que l'opérateur fait réellement quand une alarme sonne (l'observer, ne pas seulement le demander)
- [ ] Alarmes que l'opérateur déclare ignorer, et pourquoi
- [ ] Alarmes actives au moment de la visite : nombre, ancienneté
- [ ] Documentation au poste : fiches réflexes, consignes, numéros d'astreinte

## 3. Les installations

- [ ] Inventaire des équipements qui produisent des alarmes ([modèle](inventaire-equipements.csv))
- [ ] Pour chacun : ce qui remonte en supervision (tout, défaut général seulement, rien)
- [ ] Systèmes packagés avec leurs propres alarmes locales
- [ ] Liaisons par contacts secs : quels contacts, quelle signification
- [ ] Automates dont le programme n'est pas disponible
- [ ] Synchronisation des horloges (supervision, automates, systèmes packagés)

## 4. Les codes et messages inconnus

Pour chaque code ou message dont personne ne connaît le sens :

- [ ] Code exact et équipement source relevés
- [ ] Recherche dans la documentation constructeur
- [ ] Question posée au fournisseur ou au mainteneur
- [ ] Si nécessaire et autorisé : essai contrôlé avec l'exploitation pour confirmer la signification
- [ ] Résultat inscrit dans le [registre des alarmes](base-alarmes-maitre.csv), avec la **source** de l'information et la date de vérification

Une information sans source n'est pas une information : c'est une rumeur qui finira dans une consigne.

## 5. Gestion et organisation

- [ ] Qui peut modifier un seuil, une priorité, une inhibition
- [ ] Les accès sont-ils nominatifs ou partagés
- [ ] Existe-t-il une procédure de modification, et est-elle appliquée aux alarmes
- [ ] Comment les intervenants extérieurs préviennent-ils l'exploitation avant des travaux ([modèle](notification-intervention-tiers.md))
- [ ] Contrats de maintenance : périmètre, délais d'intervention, astreinte

## 6. Avant de partir

- [ ] Premières observations restituées à l'exploitation, oralement
- [ ] Signaux d'alerte immédiats signalés par écrit (alarme de protection figée, inhibition sans trace)
- [ ] Données collectées listées, emplacement de stockage convenu
- [ ] Prochaine étape et date fixées
