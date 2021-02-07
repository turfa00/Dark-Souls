* On doit implémenter un programme qui va permettre à un maximum de 4 joueurs/IA de jouer au jeu du Labyrinthe.
* Pour ce faire, nous devons résoudre plusieurs sous-problèmes:
*   - Identifier les joueurs
*       - Combien sont-ils?
*           - Le nombre d'humains nous donnera le nombre d'IA. Donc nouveau problème: programmer une IA
*               - Faire en sorte que l'IA puisse jouer intelligemment
*                    - Faire en sorte qu'elle puisse analyser tous les coups possibles et choisir le plus optimal
*       - Qui sont-ils?
*           - Donner la possibilité aux joueurs de choisir le pseudo et la couleur
*           - Assigner un pion à chaque joueur
*   - Créer le plateau
*       - Placer aléatoirement les cases (chemin, trésor)
*           - Définir tous les différents types de cases
*       - Bloquer une rangée sur deux
*   - Définir tous les coups qu'il est possible de faire
*       - Permettre de pousser une rangée de tuiles non bloquées, dans les deux sens.
*           - Décaler chaque case. La première case sera celle insérée, et la dernière case sortira du plateau et sera la prochaine à être insérée.
*       - Permettre ou non au pion de se déplacer
*           - Lier toutes les cases compatibles pour créer un chemin
*       (WIP)
