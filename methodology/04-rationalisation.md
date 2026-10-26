# 04 · Rationalisation

La rationalisation est la revue **alarme par alarme** de ce qui justifie chaque alarme, de sa priorité et de son réglage. C'est l'étape qui produit le résultat. Les indicateurs ne servent qu'à choisir par où commencer.

## Par où commencer

On ne rationalise pas 800 alarmes d'un coup. Dans l'ordre :

1. les **alarmes figées** liées à une protection ou à la sécurité (urgence) ;
2. le **top 10** des alarmes les plus fréquentes ;
3. les **alarmes intermittentes et fugitives** ;
4. les **causes des avalanches** et leurs conséquences ;
5. le reste, par zone ou par système, à rythme régulier.

Les trois premiers points règlent en général l'essentiel de la charge en une ou deux demi-journées d'atelier.

## L'atelier

- **Participants** : un opérateur expérimenté, la maintenance, l'automaticien ou l'intégrateur, la personne qui valide les conséquences (qualité, sécurité, environnement selon l'alarme), un animateur.
- **Durée** : séances de 2 à 3 heures. Au-delà, la qualité des décisions baisse.
- **Support** : le [registre des alarmes](../templates/base-alarmes-maitre.csv) projeté, une ligne remplie par alarme traitée.
- **Règle** : chaque décision est écrite, avec sa justification, au moment où elle est prise.

## Les questions à poser pour chaque alarme

| # | Question | Colonne du registre |
|---|---|---|
| 1 | Qu'est-ce qui déclenche cette alarme ? Quelle est sa cause la plus probable ? | cause_probable |
| 2 | Que se passe-t-il si personne ne réagit ? | consequence_si_inaction, gravite |
| 3 | Que doit faire l'opérateur, concrètement ? | action_operateur |
| 4 | De combien de temps dispose-t-il avant que la conséquence se produise ? | delai_reponse_admissible_min |
| 5 | Quelle priorité, d'après la matrice ? | priorite |
| 6 | Le seuil laisse-t-il le temps d'agir ? La bande morte et la temporisation sont-elles adaptées ? | seuil, bande_morte, tempo_apparition_s |
| 7 | L'alarme doit-elle être inhibée dans certains états (arrêt, nettoyage, maintenance) ? | suppression_conditionnee |

Si la réponse à la question 3 est « rien », l'alarme n'en est pas une. Si la réponse à la question 4 dépasse largement la durée d'un poste, un ordre de maintenance ou un rapport conviennent mieux.

## Attribuer la priorité

La priorité dépend de **deux** choses : la gravité de la conséquence et le délai dont dispose l'opérateur. Pas de l'importance ressentie de l'équipement, ni de la personne qui a demandé l'alarme.

Matrice d'exemple et grille de gravité à adapter : [matrice-priorite.md](../templates/matrice-priorite.md).

Contrôle de cohérence : à la fin de la rationalisation, la répartition doit tendre vers environ 80 % de priorité basse, 15 % de moyenne et 5 % de haute (en nombre d'alarmes annoncées). Si ce n'est pas le cas, la matrice est mal calibrée ou mal appliquée.

## Arbre de décision

```
L'alarme correspond-elle à une situation anormale ?
├── Non → convertir en événement ou en information d'état
└── Oui → L'opérateur a-t-il une action à faire ?
    ├── Non → convertir en événement, en rapport ou en ordre de maintenance
    └── Oui → Une autre alarme annonce-t-elle déjà la même chose ?
        ├── Oui → supprimer le doublon, garder celle qui arrive en premier
        └── Non → Apparaît-elle dans un état normal (arrêt, nettoyage, démarrage) ?
            ├── Oui → suppression conditionnée à l'état
            └── Non → Oscille-t-elle ou revient-elle en quelques secondes ?
                ├── Oui → bande morte et/ou temporisation
                └── Non → Est-elle figée ?
                    ├── Oui → maintenance du capteur, ou revoir la définition
                    └── Non → conserver, documenter, rédiger la fiche réflexe
```

## Traitements types des alarmes nuisibles

| Problème | Traitement | Point d'attention |
|---|---|---|
| Alarme qui oscille autour du seuil | Bande morte (hystérésis) | Une bande morte trop large retarde le retour et masque la répétition. |
| Pics courts sans conséquence | Temporisation à l'apparition | Vérifier que la temporisation laisse encore le temps d'agir (question 4). |
| Retour à la normale trop rapide | Temporisation à la disparition | Évite les doubles alarmes sur un même événement. |
| Alarme attendue dans un état normal | Suppression conditionnée à l'état (machine arrêtée, phase de nettoyage) | La condition doit être fiable ; documenter la logique. |
| Cascade de conséquences | Suppression des conséquences tant que la cause est active, ou alarme de synthèse | Ne jamais supprimer une conséquence qui demande une action différente. |
| Défaut d'instrument ou de communication | Classe « diagnostic », présentation séparée, regroupement | Il reste à traiter : c'est souvent une protection aveugle. |
| État présenté comme une alarme | Conversion en événement ou en indicateur | L'information reste disponible, elle ne sollicite plus l'opérateur. |

Points de départ couramment cités pour les réglages (ISA-18.2), **à valider sur le procédé** :

| Type de mesure | Bande morte | Temporisation |
|---|---|---|
| Débit | 5 % de l'étendue | 15 s |
| Niveau | 5 % de l'étendue | 60 s |
| Pression | 2 % de l'étendue | 15 s |
| Température | 1 % de l'étendue | 60 s |

## Inhiber proprement

Trois mécanismes à ne pas confondre :

- **Mise en attente temporaire** (*shelving*) : un opérateur retire une alarme de l'affichage pour une durée limitée, avec trace et retour automatique.
- **Suppression par conception** : l'alarme est inhibée automatiquement dans un état défini (machine arrêtée, phase de nettoyage). La logique est documentée et testée.
- **Mise hors service** : l'alarme est désactivée, par exemple pendant une réparation. Elle suit la gestion des modifications et une mesure compensatoire est définie.

Une inhibition sans durée, sans trace et sans responsable est la façon la plus courante de perdre une protection sans s'en rendre compte.

## Ce qui ne se rationalise pas en atelier

Les alarmes créditées comme barrière dans une analyse de risques (HAZOP, LOPA) et les fonctions de sécurité instrumentées relèvent de leur propre démarche. L'atelier peut signaler un problème (alarme figée, temps de réponse irréaliste), mais la décision appartient au propriétaire de l'analyse de risques.

## Livrables

- le [registre des alarmes](../templates/base-alarmes-maitre.csv) complété pour chaque alarme traitée ;
- un plan d'action : modification, responsable, échéance, gain attendu ;
- les [fiches réflexes](../templates/fiche-reflexe-operateur.md) des alarmes conservées les plus fréquentes ou les plus graves.
