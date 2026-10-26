# Analyse · LactoDémo SA (site fictif)

> Données entièrement fictives. Les chiffres proviennent du [calculateur](../tools/calcul-indicateurs-alarmes.xlsx) appliqué au [journal d'exemple](journal-alarmes-fictif.csv). Le gain du plan d'action est une **estimation**, obtenue en rejouant le journal avec les modifications proposées.

## 1. Synthèse

Sur une semaine, l'unique opérateur de la salle de contrôle a reçu **1 336 alarmes**, soit **191 par jour**. La moyenne se situe entre la valeur acceptable (env. 150) et le maximum gérable (env. 300). Elle donne une impression trompeuse : la structure de la charge est profondément déséquilibrée.

- **Dix tags produisent 87 % des alarmes.** Une seule chambre froide en produit un tiers.
- **Deux avalanches réelles** ont noyé l'opérateur : jusqu'à **44 alarmes en 10 minutes** après le déclenchement de la chaudière.
- **Neuf autres « avalanches »** n'ont aucune cause d'exploitation : elles sont produites par deux alarmes intermittentes.
- **Un détecteur de niveau très haut est bloqué toute la semaine.** La protection contre le débordement du tank 3 est aveugle.
- **Plus d'un tiers des alarmes sont en priorité haute**, contre environ 5 % attendus.

Deux réparations urgentes et sept modifications de configuration réduiraient la charge d'environ **84 %**, à une trentaine d'alarmes par jour, sans avalanche.

## 2. Indicateurs

| Indicateur | Valeur | Référence | Statut |
|---|---|---|---|
| Alarmes annoncées sur 7 jours | 1 336 | | |
| Tags distincts | 33 | | |
| Alarmes par jour | 191 | env. 150 / 300 max. | À surveiller |
| Alarmes par heure | 8,0 | env. 6 / 12 max. | À surveiller |
| Alarmes par 10 minutes | 1,33 | env. 1 | À surveiller |
| Maximum en 10 minutes | 44 | 10 | Hors cible |
| Fenêtres de 10 min en avalanche | 1,2 % (12 fenêtres) | moins de 1 % | Hors cible |
| Heures avec plus de 30 alarmes | 1,2 % (2 heures) | moins de 1 % | Hors cible |
| Part du top 10 | 87,1 % | 1 à 5 % | Hors cible |
| Tags intermittents | 6 (416 activations, 31 % de la charge) | aucun | Hors cible |
| Tags fugitifs | 7 (100 activations) | aucun | Hors cible |
| Tags figés plus de 24 h | 2 | moins de 5, avec plan d'action | À surveiller |
| Priorité haute / moyenne / basse | 36 % / 28 % / 36 % | env. 5 / 15 / 80 % | Hors cible |

Charge par jour : lundi 213, mardi 187, mercredi 260, jeudi 173, vendredi 188, samedi 250, dimanche 65. Les deux jours les plus chargés sont ceux des incidents.

*Remarque : avec 33 tags seulement, la part du top 10 reste élevée par construction, même après correction. Sur un petit système, on regarde surtout le volume absolu du top 10.*

## 3. Le top 10

| Rang | Tag | Description | Priorité | Activations | Cumul | Diagnostic |
|---|---|---|---|---|---|---|
| 1 | FR02_TT01_H | Chambre froide 2 - température haute | Haute | 431 | 32 % | Intermittente et fugitive. Oscille autour du seuil, aucune bande morte. |
| 2 | AIR_PT01_L | Air comprimé - pression réseau basse | Moyenne | 178 | 46 % | Intermittente. Creux de pression au démarrage du deuxième compresseur. |
| 3 | CND_ST04_ARR | Conditionneuse 4 - machine à l'arrêt | Basse | 162 | 58 % | État normal présenté comme une alarme. |
| 4 | CND_ST02_ARR | Conditionneuse 2 - machine à l'arrêt | Basse | 92 | 65 % | Idem. |
| 5 | FR01_PORTE | Chambre froide 1 - porte ouverte > 5 min | Moyenne | 73 | 70 % | Alarme légitime, fréquence liée aux pratiques de chargement. |
| 6 | NEP_TT02_L | NEP - température retour basse | Basse | 55 | 74 % | Intermittente et fugitive, attendue à chaque début de cycle. |
| 7 | CND_ST01_ARR | Conditionneuse 1 - machine à l'arrêt | Basse | 54 | 78 % | État normal présenté comme une alarme. |
| 8 | REC_FT01_DEV | Réception - écart débitmètre / bon de livraison | Basse | 52 | 82 % | Information administrative, aucune action en temps réel. |
| 9 | NEP_CT01_L | NEP - conductivité soude basse | Moyenne | 39 | 85 % | Attendue pendant la montée en concentration. |
| 10 | CND_ST04_DEF | Conditionneuse 4 - défaut film | Moyenne | 27 | 87 % | Alarme légitime, à revoir lors de la prochaine itération. |

Huit de ces dix alarmes ne demandent aucune action de l'opérateur au moment où elles apparaissent. C'est le constat central du diagnostic.

## 4. Les avalanches

Douze fenêtres de 10 minutes dépassent 10 alarmes. Seules trois correspondent à un incident réel.

### Mercredi 4 mars, déclenchement de la chaudière

La cause apparaît à 10 h 47 min 12 s : `CHD_TRIP`. Dans les 10 minutes qui suivent, l'opérateur reçoit **59 alarmes provenant de 18 tags**. La fenêtre fixe de 10 h 50 en compte 44 à elle seule.

Les alarmes les plus nombreuses de la séquence ne sont pas les conséquences de la perte de vapeur, mais des alarmes perturbatrices que l'incident a réveillées : défaut de transmetteur du pasteurisateur (14 fois), débit de retour NEP (10), chambre froide 2 (9), air comprimé (8), communication automate (5). L'alarme utile, celle qui dit « la chaudière a déclenché », est une ligne parmi 59.

À noter : la fenêtre de 10 h 40 contient le début de la séquence, mais sa première alarme est un filtre à air colmaté sans rapport avec l'incident. Une avalanche à cheval sur deux fenêtres se lit sur les deux.

### Samedi 7 mars, micro-coupure réseau

Cause à 6 h 02 min 37 s : `ELEC_RES_DEF`, suivie de `ELEC_UPS_BAT`. En 10 minutes, **35 alarmes de 16 tags**, dont 12 pertes de communication avec les automates 3 et 5 et 7 activations de la chambre froide 2.

### Les fausses avalanches

Neuf fenêtres dépassent 10 alarmes **sans aucun incident d'exploitation**. Elles sont produites par `FR02_TT01_H` et `AIR_PT01_L`, qui s'activent en rafales. Dont une, lundi à 3 h 10, en pleine nuit : 12 activations de la chambre froide 2 en 10 minutes.

## 5. Les alarmes figées

| Tag | Active depuis | Durée | Lecture |
|---|---|---|---|
| TK03_LSH · Tank lait cru 3 - niveau très haut | lundi 3 h 12 | toute la semaine, toujours active | Détecteur bloqué. **La protection contre le débordement du tank 3 ne fonctionne plus.** Les opérateurs ont appris à l'ignorer. |
| STEP_AT01_L · STEP - pH effluent bas | mercredi 9 h 40 | environ 60 heures | Sonde de pH en dérive. Pendant deux jours et demi, un rejet réellement acide n'aurait pas été distingué de la dérive. |

Ces deux alarmes pèsent deux lignes sur 1 336. Ce sont pourtant les deux constats les plus importants du diagnostic.

## 6. Les priorités

36 % des alarmes sont en priorité haute. L'essentiel vient de `FR02_TT01_H`, classée haute à sa création et responsable à elle seule de 431 activations. Quand l'alarme la plus bruyante du site est aussi la plus prioritaire, l'opérateur apprend que « haute » ne veut rien dire.

## 7. Rationalisation des alarmes traitées

Décisions prises en atelier (fictif), selon la [méthode](../methodology/04-rationalisation.md) et la [matrice de priorité](../templates/matrice-priorite.md).

| Tag | Conséquence si inaction | Délai | Décision | Priorité avant → après |
|---|---|---|---|---|
| TK03_LSH | Débordement de lait cru, rejet vers les eaux usées (grave) | moins de 5 min | **Urgent** : remise en état du détecteur, test fonctionnel, mesure compensatoire immédiate (surveillance du niveau continu, consigne de dépotage). Test périodique à planifier. | Haute → Haute |
| STEP_AT01_L | Rejet hors limite, déclaration obligatoire (grave) | 5 à 15 min | **Urgent** : réparation et étalonnage de la sonde. Ajout d'une détection de défaut de sonde (valeur figée ou écart). | Haute → Haute |
| FR02_TT01_H | Produit au-dessus de la température de conservation, lot à déclasser (significative) | 15 à 30 min | Bande morte de 0,5 K, temporisation de 120 s, fiche réflexe | Haute → Moyenne |
| AIR_PT01_L | Défaillance des vannes pneumatiques si la baisse dure (significative) | 5 à 15 min | Temporisation de 30 s, seuil placé sous la plage de régulation. Vérifier la cascade des compresseurs. | Moyenne → Moyenne |
| CND_ST01/02/04_ARR | Aucune : arrêt normal, visible sur la ligne | sans objet | Converties en événements, utilisées pour le suivi de performance des lignes | Basse → événement |
| NEP_TT02_L, NEP_CT01_L, NEP_FT01_L | Nettoyage insuffisant si l'étape échoue (significative) | 15 à 30 min | Inhibées pendant la phase de montée. Remplacées par une alarme unique d'échec d'étape, générée par l'automate si les critères de l'étape ne sont pas atteints. | Basse et moyenne → une alarme Moyenne |
| REC_FT01_DEV | Écart administratif sur la quantité livrée | plus de 30 min | Converti en rapport quotidien de réception | Basse → rapport |
| PAS_TT05_TRANS, SUP_COM_PLC03/05 | Mesure ou commande indisponible | variable | Classe « diagnostic », regroupement des répétitions sur 5 minutes | inchangée |
| CHD_TRIP, ELEC_RES_DEF (causes d'avalanche) | Perte d'utilités | moins de 5 min | Première alarme mise en évidence. Les conséquences attendues (températures pasteurisateur et NEP, pression vapeur, eau glacée, ventilation, air comprimé, chambre froide 2) sont inhibées pendant 15 minutes après la cause. Les alarmes qui demandent une action différente (différentiel de pression du pasteurisateur, défauts nécessitant un réarmement) restent actives. | Haute → Haute |

Exemple de fiche réflexe rédigée pour `FR02_TT01_H` : [fiche-reflexe-operateur.md](../templates/fiche-reflexe-operateur.md). Deux lignes du registre sont remplies à titre d'exemple dans [base-alarmes-maitre.csv](../templates/base-alarmes-maitre.csv).

## 8. Plan d'action et gain estimé

| # | Action | Nature | Activations évitées sur la semaine |
|---|---|---|---|
| U1 | Remise en état et test du détecteur TK03_LSH, mesure compensatoire | Maintenance, **immédiat** | sans objet : c'est une question de sécurité, pas de charge |
| U2 | Réparation et étalonnage de la sonde STEP_AT01_L, détection de défaut de sonde | Maintenance, **immédiat** | sans objet |
| A1 | FR02_TT01_H : bande morte et temporisation | Configuration | 431 |
| A2 | AIR_PT01_L : temporisation | Configuration | 177 |
| A3 | Arrêts des conditionneuses convertis en événements | Configuration | 308 |
| A4 | NEP : inhibition en phase de montée, alarme unique d'échec d'étape | Automate | 120 |
| A5 | Écart de réception converti en rapport | Configuration | 52 |
| A6 | Défauts transmetteur et communication : regroupement | Configuration | 30 |
| A7 | Inhibition des conséquences après une cause d'avalanche | Automate | 10 |
| | **Total** | | **1 128 sur 1 336** |

Résultat estimé en rejouant la semaine avec ces modifications :

| Indicateur | Avant | Après (estimation) |
|---|---|---|
| Alarmes sur la semaine | 1 336 | 208 |
| Alarmes par jour | 191 | 30 |
| Maximum en 10 minutes | 44 | 8 |
| Fenêtres en avalanche | 12 | 0 |

Dans ce jeu de données, toutes les activations de `FR02_TT01_H` étaient des oscillations de moins de deux minutes : la temporisation les supprime toutes. Sur un site réel, les vraies dérives de température resteraient visibles, et c'est précisément le but. L'alarme unique d'échec d'étape NEP ajouterait quelques alarmes en cas d'échec réel, qui ne se produit pas dans la semaine fictive.

## 9. Et ensuite

Après correction, le nouveau top 3 serait `FR01_PORTE` (73), `CND_ST04_DEF` (26) et `HVAC_CND_HR` (21). Ce sont des alarmes légitimes : leur fréquence parle des pratiques de chargement, de l'approvisionnement en film et de la ventilation. C'est le sujet de la deuxième itération, avec l'exploitation.

Côté organisation :

1. rédiger une première philosophie d'alarme à partir des décisions de l'atelier ([trame](../templates/philosophie-alarmes-modele.md)) ;
2. compléter le registre pour les 33 tags ;
3. mettre en place la revue mensuelle des indicateurs ;
4. imposer les questions de rationalisation aux intégrateurs pour toute nouvelle alarme.

## 10. Limites de cet exemple

- Le journal est synthétique. Il reproduit des situations courantes, pas un site réel.
- Le gain est estimé en supprimant des lignes du journal selon des règles simples. Sur un site réel, chaque modification se teste et se mesure après mise en œuvre.
- Les priorités « après » sont le résultat d'un atelier fictif. Sur un site réel, elles se décident avec l'exploitation, la qualité et la sécurité.
