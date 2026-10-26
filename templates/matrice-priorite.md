# Matrice de priorité

La priorité d'une alarme dépend de **la gravité de la conséquence** si personne ne réagit et du **délai dont dispose l'opérateur** pour agir. Cette matrice est un **exemple à calibrer** pour votre site, puis à inscrire dans votre philosophie d'alarme.

## 1. Gravité de la conséquence

Retenez la gravité la plus élevée parmi les domaines concernés. Les seuils chiffrés sont des exemples : adaptez-les à la taille et à l'activité du site.

| Domaine | Mineure | Significative | Grave |
|---|---|---|---|
| Personnes | Aucun risque de blessure | Blessure légère possible | Blessure grave possible |
| Environnement | Aucun rejet | Rejet ponctuel maîtrisé, sans dépassement de limite | Rejet hors limite autorisée, déclaration obligatoire |
| Qualité, sécurité des produits | Aucun impact produit | Lot à contrôler ou à déclasser | Produit non conforme susceptible d'être libéré |
| Production, coûts | Perte inférieure à CHF 1'000 ou arrêt de moins d'une heure | Perte jusqu'à CHF 20'000 ou arrêt de moins d'une journée | Perte supérieure, ou arrêt de plus d'une journée |
| Équipement | Usure normale | Dommage réparable sur site | Dommage majeur, remplacement |

## 2. Délai de réponse admissible

Temps entre l'apparition de l'alarme et le moment où la conséquence devient inévitable, **moins** le temps nécessaire pour exécuter l'action. Si l'opérateur doit se déplacer, comptez le déplacement.

## 3. Matrice

| Délai de réponse admissible | Mineure | Significative | Grave |
|---|---|---|---|
| moins de 5 min | Moyenne | Haute | Haute |
| 5 à 15 min | Basse | Moyenne | Haute |
| 15 à 30 min | Basse | Moyenne | Moyenne |
| plus de 30 min | Pas une alarme* | Basse | Moyenne |

\* À traiter comme message, rapport ou ordre de maintenance.

## 4. Contrôles de cohérence

- **Répartition cible** sur l'ensemble des alarmes annoncées : environ 80 % basse, 15 % moyenne, 5 % haute. Un écart important signale une matrice mal calibrée ou appliquée par habitude.
- **Pas d'alarme sans action.** Si la question « que fait l'opérateur ? » reste sans réponse, la matrice ne s'applique pas : ce n'est pas une alarme.
- **Délai irréaliste.** Si le délai est inférieur au temps nécessaire pour comprendre et agir, une alarme ne suffit pas. Il faut une protection automatique, à traiter dans l'analyse de risques.
- **Barrières créditées.** Les alarmes créditées dans une analyse de risques suivent les exigences de cette analyse, quelle que soit la matrice.

## 5. Conventions de présentation (exemple)

| Priorité | Couleur | Son | Attente vis-à-vis de l'opérateur |
|---|---|---|---|
| Haute | Rouge | Distinct, répété jusqu'à l'acquittement | Action immédiate, tout le reste attend |
| Moyenne | Orange ou jaune | Distinct, une fois | Action rapide, dans le délai indiqué |
| Basse | Jaune pâle ou cyan | Discret ou aucun | Action dans le poste |

Réservez les couleurs d'alarme aux alarmes. Si le rouge sert aussi à afficher « vanne fermée » ou « moteur arrêté », il perd son sens.
