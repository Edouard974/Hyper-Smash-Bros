# Hyper Smash Bros.

Basé sur le projet Hyper Smash Bros. des Super Coding Bros. pendant les Coding Weeks 2021 de CentraleSupélec.

Lien vers la démo : https://www.youtube.com/watch?v=54JSfYjeWTA 

## Les Super Coding Bros.

- Membres 1,2 : Edouard Seguier, Maxime Chambre |=> Gameplay : mécaniques de combat, animations de combat
- Membre 3 : Benjamin Bigot => Interface, menus
- Membre 4 : Paul Schoenecker => animations de combat et tutoriel
- Membre 5 : Pierre-Emmanuel => tutoriel

## Description du jeu

Le but principal de chaque Super Smash Bros. est de se combattre afin d'envoyer les adversaires hors de l'arène. Pour cela, il faut attaquer l'ennemi à plusieurs reprises pour faire augmenter son pourcentage de dégâts. Plus celui-ci est élevé, plus les ennemis voleront loin à la porté des coups et sortiront éventuellement de l'écran.

Le gameplay de la série propose un mélange de jeu de combat et de jeu de plates-formes. En effet, le principe des jeux de combats classiques dans lequel les joueurs font des combinaisons de boutons pour faire plusieurs attaques différentes est fusionné avec un aspect plates-formes dans lequel les joueurs doivent déplacer leurs personnages partout dans l'arène et doivent parfois sauter sur des plates-formes.

## Bibliothèques à importer

pygame : permet d'ajouter des effets sonores et musiques de fond
time : permet d'incorporer la notion de temps
os : permet d'importer des images
sys : permet de fermer le jeu
random : pour pouvoir choisir aléatoirement un personnage ou stage
math : fonctions usuelles cos, exp pour modéliser des mouvements

## Instructions pour jouer

- Lancer le fichier init.py
- Selectionner le mode voulu :
        - à l'aide de la touche A avec navigation avec ZQSD (pour le joueur 1)
        - à l'aide de la touche CTRL droite avec navigation avec les flèches directionnelles (pour le joueur 2)

## Commandes

- Joueur 1 :\
        Movement - ZQSD\
        Attack - E\
        Jump - A\
        Shield - F\
        Grab - R\
        Special - T

- Joueur 2 :\
        Movement - flèches directionnelles\
        Attack - CTRL droite\
        Jump - SHIFT\
        Grab - ENTER\
        Shield - :\
        Special - ;

## Règles et mécaniques de jeu

-Chaque joueur dispose de 4 vies.\
-Le match se déroule sur un terrain avec choix de platformes ou non entouré de vide ; le joueur perd une vie si il est éjecté hors de l'écran ou si il tombe dans le vide.

### MOUVEMENTS

- Double saut : Chaque joueur peut sauter puis double sauter en l'air.
- Dash : [appuyer 2 fois rapidement dans la même direction] le joueur peut se mouvoir plus vite.
- Bouclier (shield) : [Bouclier au sol] rend le joueur invincible aux attaques normales.
- Esquive : [Bouclier + direction latérale au sol] rend le joueur complètement invincible et performe un mouvement latéral.
- Esquive aérienne (airdodge) : [Bouclier en l'air] rend le joueur invincible pendant une courte période, suivie d'une période de vulnérabilité.
- Walljump : [direction opposée au mur lorsque le joueur est collé au mur] performe un saut supplémentaire

### LEDGE (rebord)
Quatre options :
- Neutral get up : [direction haut ou vers le terrain] 
- Ledge roll : [bouclier] permet au joueur de se relever et de faire une esquive sur le terrain
- Ledge Jump : [saut] performe un saut à partir du rebord
- Legde Drop : [direction bas ou opposée au terrain] lâche le rebord du terrain

### ATTAQUES
5 attaques sont à disposition du joueur, et leur propriétés varient en fonction du personnage joué. Chaque coup met un certain temps à se déclencher (temps dit de "startup"), crée une boite de collision active pendant un court temps ("active frames"), et laisse le joueur vulnérable pendant un certain temps à la fin ("endlag") :
- Le up-tilt [Attack + direction vers le haut] est généralement rapide et permet de toucher un adversaire au dessus de soi.
- Le forward-tilt [Attack ou Attack + direction sur le coté] est l'attaque 'usuelle' la plus aisée à placer.
- Le down-air [Attack + direction vers le bas, en l'air] éjecte l'adversaire vers le bas, et est utilisé poir l'empêcher de revenir sur le terrain.
- L'attaque spéciale [Special] dépend du personnage joué, mais est généralement un projectile.
- Le grab [Grab] est une attaque de courte portée permettant d'attraper l'ennemi. C'est la seule attaque ignorant le bouclier adverse. Une fois l'ennemi attrapé, il peut être lancé dans une direction quelconque en appuyant vers la direction correspondante.

### PRINCIPE TRIANGULAIRE
Le bouclier permet de se défendre des attaques.\
Le grab permet de vaincre le bouclier.\
Les attaques battent le grab.

### HITSTUN ET KNOCKBACK, FORMULES

Le hitstun est le temps durant lequel le joueur est incapable d'agir après avoir encaissé une attaque.\
Il est calculé de la manière suivante :

                                hitstun = base_hitstun + global_hitstun*(1-exp(-percent/33))

Avec:   -'base_histun' le hitstun minimal, qui dépend de chaque attaque.\
        -'global_hitstun' le coefficient global d'augmentation du histun en fonction des pourcentages.\
        -'percent' les pourcentages  du joueur.

Pour des raisons d'équilibrages, il est en effet nécéssaire que les attaques incapacitent l'adversaire même à 0%.\
Ceci dit, pour rendre le jeu dynamique, les joueurs ne devraient pas être incapacités trop longtemps, d'ou l'exponentielle.

Le knockback est la force de l'éjection subie par le joueur après avoir encaissé une attaque.\
Il est calculé de la manière suivante :

                                knockback = base_knockback*(1 + percent/80)


## Copyrights

The concept of the game is the property of Nintendo, HAL Laboratory, Sora Ltd. and Bandai Namco Games, so are also the sounds and the images.
This project is for educational purpose only.
