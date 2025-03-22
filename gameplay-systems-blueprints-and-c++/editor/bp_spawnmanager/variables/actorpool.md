---
description: Volumes définissant les zones valides pour le spawn dynamique.
icon: table-cells
---

# ActorPool

#### Description générale

`ActorPool` est une variable de type **Array d'objets**, contenant des références aux instances d’acteurs (`Actor`) pré-créés et disponibles pour être réutilisés par le système de pooling. Elle est utilisée pour stocker et gérer les acteurs inactifs qui pourront être réactivés au lieu d'être recréés, permettant ainsi d'améliorer les performances du jeu.

***

#### Détails techniques

| Propriété                      | Valeur                                 |
| ------------------------------ | -------------------------------------- |
| **Nom de la variable**         | ActorPool                              |
| **Type**                       | Array d'objets : `Actor`               |
| **Catégorie**                  | Par défaut                             |
| **Instance modifiable**        | Non                                    |
| **Blueprint en lecture seule** | Non                                    |
| **Exposer à l’apparition**     | Non                                    |
| **Privé**                      | Non (accessible aux autres Blueprints) |
| **Réplicable**                 | Non                                    |
| **Condition de réplication**   | Aucune                                 |
| **Valeur par défaut**          | Initialisée vide (0 élément)           |

***

#### Comportement

* **Gestion dynamique** : `ActorPool` contient les acteurs prêts à être utilisés par le système de spawn lorsqu'il est configuré en mode pooling.
* **Non modifiable à l’instanciation** : Elle est remplie en amont (par exemple au lancement du niveau) ou dynamiquement durant l'exécution.
* **Locale** : Pas de réplication par défaut — le contenu du pool reste local au client ou au serveur.

***

#### Utilisation prévue

`ActorPool` est utilisée pour :

* Stocker des instances d’acteurs désactivés ou cachés, prêts à être réutilisés sans recréation.
* Éviter la surcharge due à la destruction et instanciation répétée d’acteurs.
* Travailler en combinaison avec la variable **bUsePooling** pour activer/désactiver dynamiquement l'utilisation du pool.

Chaque acteur du pool peut être configuré pour être désactivé visuellement (hidden) ou désactivé logiquement (disabled), puis réactivé au moment du besoin.

***

#### Bonnes pratiques

* **Validation** : Toujours vérifier la validité des références avant de tenter d’utiliser un acteur depuis le pool.
* **Nettoyage** : Retirer proprement les références des acteurs détruits ou invalides pour éviter des erreurs.
* **Remplissage initial** : Remplir le pool dès le lancement du niveau si nécessaire, avec un nombre défini d’acteurs pour anticiper les besoins.
* **Taille optimale** : Ajuster la taille du pool selon le profil de la scène (ni trop petit pour éviter le manque, ni trop grand pour préserver la mémoire).
* **Documentation** : Ajouter une description explicite dans Unreal pour clarifier son rôle.

***

#### Suggestions d’améliorations

| Suggestion                     | Détail                                                                                                   |
| ------------------------------ | -------------------------------------------------------------------------------------------------------- |
| **Catégorisation**             | Créer une catégorie personnalisée (ex. : \`Gameplay                                                      |
| **Description**                | Ajouter une description dans Unreal précisant qu'il s'agit du conteneur principal du système de pooling. |
| **Blueprint en lecture seule** | Activer si la variable est uniquement gérée par le système de spawn, sans modifications externes.        |
| **Réplicabilité future**       | Envisager la réplication si le pool doit être partagé ou synchronisé dans un contexte multijoueur.       |

***

#### Exemple visuel _(pour ton GitBook si besoin)_ :

* Diagramme illustrant le cycle des acteurs : **Spawn → Utilisation → Désactivation → Retour au pool**.
* Capture d’écran montrant l’utilisation de `ActorPool` dans une boucle ou une logique de récupération d’acteurs.

***

#### Remarque

**ActorPool** fonctionne étroitement avec les variables **bUsePooling**, **SpawnedActors**, et **MaxSpawnedActors** pour mettre en place un système de spawn performant, optimisé, et flexible.
