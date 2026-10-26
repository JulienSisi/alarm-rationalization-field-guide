# Philosophie d'alarme · [Nom du site]

> Trame à compléter. Objectif : 6 à 12 pages. Un document court et appliqué vaut mieux qu'un document complet que personne n'ouvre. Supprimez les indications entre crochets une fois le texte rédigé.

| Version | Date | Rédigé par | Approuvé par | Modifications |
|---|---|---|---|---|
| 1.0 | [date] | [nom, fonction] | [nom, fonction] | Création |

## 1. Objet et périmètre

- Objet : fixer les règles de conception, d'exploitation et de suivi des alarmes du site.
- Périmètre : [postes opérateur, systèmes de supervision, automates et systèmes packagés concernés].
- Hors périmètre : [par exemple fonctions de sécurité instrumentées, détection incendie, intrusion], qui relèvent de [référence].
- Documents de référence : IEC 62682, ANSI/ISA-18.2, EEMUA 191, [analyses de risques du site], [procédure de gestion des modifications].

## 2. Définitions

- **Alarme** : signal annonçant à l'opérateur un dysfonctionnement, une dérive ou une situation anormale qui exige une réponse de sa part dans un délai donné.
- **Événement** : information enregistrée qui ne demande pas d'action immédiate.
- **Mise en attente temporaire**, **suppression par conception**, **mise hors service** : [définir selon la section 8].
- [Autres termes utilisés sur le site.]

## 3. Rôles et responsabilités

| Rôle | Responsabilité | Titulaire |
|---|---|---|
| Responsable du système d'alarmes | Tient le registre, suit les indicateurs, anime les revues | [nom] |
| Exploitation | Utilise les alarmes, signale les alarmes inutiles, valide les actions opérateur | [nom] |
| Maintenance | Teste et répare les capteurs et les alarmes | [nom] |
| Automatisme / intégrateur | Réalise les modifications validées | [nom ou société] |
| Qualité, sécurité, environnement | Valide les conséquences et priorités dans son domaine | [nom] |

## 4. Critères d'une alarme

Une alarme n'est créée ou conservée que si les trois conditions sont réunies :

1. elle signale une situation anormale ;
2. elle demande une action définie de l'opérateur ;
3. cette action doit être réalisée dans un délai défini.

Sinon : événement, message, rapport ou ordre de maintenance.

## 5. Priorités

- Nombre de niveaux : [3 recommandés].
- Méthode d'attribution : matrice gravité et délai de réponse, [référence à la matrice en annexe].
- Répartition cible : environ 80 % basse, 15 % moyenne, 5 % haute.

## 6. Classes d'alarmes

[Exemples : procédé, protection (créditée dans une analyse de risques), diagnostic d'instrumentation et de communication, qualité réglementaire. Pour chaque classe : exigences particulières de test, de modification, de traçabilité.]

## 7. Règles de conception

- Seuils : placés de façon à laisser le délai de réponse nécessaire.
- Bandes mortes et temporisations : [valeurs par défaut par type de mesure, à justifier pour toute exception].
- Textes d'alarme : [format : équipement, grandeur, sens de l'écart ; vocabulaire commun ; longueur maximale].
- Suppression conditionnée à l'état : [règles, documentation de la logique].
- Doublons : une seule alarme par situation, celle qui arrive en premier.

## 8. Présentation et inhibitions

- Couleurs et sons par priorité : [tableau].
- Mise en attente temporaire : [qui peut, durée maximale, trace, retour automatique].
- Mise hors service : [via gestion des modifications, mesure compensatoire obligatoire, liste consultable].

## 9. Indicateurs et cibles

| Indicateur | Cible du site | Fréquence de revue |
|---|---|---|
| Alarmes par jour et par poste | [150] | Mensuelle |
| Maximum d'alarmes en 10 minutes | [10] | Mensuelle |
| Temps en avalanche | [moins de 1 %] | Mensuelle |
| Part du top 10 | [à définir] | Mensuelle |
| Alarmes intermittentes et fugitives | [0] | Mensuelle |
| Alarmes figées | [moins de 5, avec plan d'action] | Hebdomadaire |
| Répartition des priorités | [80 / 15 / 5] | Annuelle |
| Inhibitions et modifications non autorisées | [0] | Trimestrielle |

## 10. Gestion des modifications

Toute création, suppression ou modification d'alarme (seuil, priorité, texte, temporisation, inhibition) suit la procédure [référence]. La modification est inscrite dans le registre des alarmes avant sa mise en service.

## 11. Formation

- Formation initiale des opérateurs : [contenu, durée].
- Fiches réflexes : [emplacement, mise à jour].
- Information après chaque lot de modifications.

## 12. Audit

[Fréquence, auditeur, périmètre : application de ce document, registre, indicateurs, gestion des modifications.]

## Annexes

- A. Matrice de priorité
- B. Registre des alarmes (référence du fichier)
- C. Liste des alarmes de protection et exigences associées
