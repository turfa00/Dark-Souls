# Fonctions:

* tableau de joueurs entrer_joueurs()
    * on crée un tableau de joueur et on l'initialise avec demander_nombre_joueurs()
    * demander_joueurs_humains(le tableau)
    * demander_couleur_joueurs(le tableau)
    * demander_pseudo_joueur(le tableau)
#

* demander_joueurs_humains(tableau de joueurs)
    * afficher "Combien d'IA?"
    * si le nombre d'IA est supérieur a demander_nombre_joueurs()-1
        + afficher "Nombre d'IA pas cohérent avec le nombre de joueurs"
    * sinon 
        + pour chaque ia
            * creer_ia(le joueur qui va devenir une ia)
#

* tableau de joueurs demander_nombre_joueurs()
    * afficher "Combien de joueurs sur cette partie?"(nbr)
    * si demander_nombre_joueurs() égal à 2, 3 ou 4
        + créer des struct joueurs en conséquence
    * sinon
        + afficher "Il n'y a pas un nombre adéquat de joueur"
#

* demander_couleur_joueurs(tableau de joueurs)
    * pour chaque joueur
        + afficher "Quelle est la couleur du joueur j.i?"(afficher les couleurs 1:Rouge, 2:Jaune...)
        + le paramètre couleur du joueur prends l'entrée clavier
#

* demander_pseudo_joueur(tableau de joueurs)
    * pour chaque joueur
        + afficher "Quel est le pseudo du joueur j.i?"
        + le paramètre nom du joueur prends l'entrée clavier
#

* changer_couleur(joueur)
    * voir https://stackoverflow.com/questions/3219393/stdlib-and-colored-output-in-c
#

* joueur creer_ia(joueur)
    * le paramètre ia du joueur passe a 1(fonction courte mais plus lisible dans le code que juste "j.ia=1")
#

* victoire_dun_joueur(joueur)
    * si case_depart(j) égal à 1(si le joueur a trouvé tous ses trésors et qu'il est retourné à son point de départ)
        + afficher_message_victoire(le joueur)
        + on sort de la boucle du main avec les jouer_tour
#

* afficher_message_victoire(joueur)
    * afficher "Le joueur j.nom a remporté la partie!"
#

* entier case_depart(joueur)
    * si le joueur a trouvé tous ses trésors et qu'il est retourné à son point de départ
        + retourne 1
    * sinon
        + retourne 0
#

* jouer_tour_ia(joueur, plateau)
    * on retourne les coups possibles avec analyse_coups_possibles_IA()
    * pour pousse la rangée choisie par l'ia avec les 2 fonctions pousser_rangee(choisir_ligne_ia(le plateau, le joueur))
    * l'ia deplace le pion avec deplacer_pion_ia()
    * on afficher un bilan de ce que l'ia viens de faire avec afficher_coup()
#

* tableau de lignes analyse_coups_possibles_IA(plateau, joueur)
    * On fait un tableau regroupant tous les coups possibles
    * (Faut trouver un moyen d'associer chaque indice du tableau à un coup, nouvelle struct?)
    * si le trésor est atteint dans une des 48 premières possibilités alors on joue ce coup
    * sinon on cherche les combinaisons de 2 coups qui permettraint d'atteindre le tresor
    * sinon on pousse une rangée au hasard qui libère un chemin et on déplace le pion sur ce chemin
#

* analyse_bloquage_possible_IA(plateau, joueur, autres joueurs(tableau de joueurs), analyse_coups_possibles_IA(le plateau, le joueur))
    * Même principe que analyse_coups_possibles_IA pour les 48 prochains coups possibles des autres joueurs, afin de savoir s'ils pourront accéder à leur trésor au prochain coup.
    * On va ensuite analyser chaque coup retenu par analyse_coups_possibles_IA et incrémenter chaque case dans le cas où le coup d'un joueur passe de 1 à 0. Le coup ayant été le plus de fois incrémentée est celle qui bloquera le plus de coups possibles chez les autres joueurs tout en permettant à l'IA d'atteindre son trésor
#

* ligne choisir_ligne_ia(plateau, joueur)
    * pour les 12 lignes:
        + si, quand on bouge la ligne, le prochain tresor est accessible
            * on retourne cette ligne
#

* deplacer_pion_ia()
    * si le prochain tresor est atteignable
        + deplacer_pion() sur le tresor
        + on passe au trésor suivant avec tresor_suivant()
    * sinon
        on reste ou on est
#

* plateau creer_plateau()
    * on crée un plateau égal à creer_cases_fixes()
    * on cree un tableau de 12 lignes égal à creer_lignes_mouvantes()
    * on assigne des indice hauteur et largeur à chaque cases pour les situer dans le plateau et on leur donne un numéro unique avec assignation_indices_cases(le tableau)
    * on place aléatoirement les cases mouvantes sur le plateau tri_aleatoire_cases_mouvantes(p)
    * on crée un tableau de trésors égal à creer_tresors()
    * on disperse aléatoirement les trésors sur le plateu avec placer_tresors(p, liste_tresors)
#

* tableau de trésors creer_tresors()
    * on crée un tableau de 24 trésors
    * pour chaque trésor:
        + on lui assigne son numéro
        + on lui assigne son nom (on prendra les noms dans un fichier)
    * on retourne le tableau
#

* placer_tresors(plateau, le tableau de trésors)
    * creer un tableau de int de taille 34, le remplir avec 0,1,2,3,4...33
    * le trier aléatoirement
    * pour les 24 tresors:
        + si la case dont le numéro correspond à l'indice n'est pas un coin
            * on associe a la case qui a le numéro correspondant le tresor de la liste
        + sinon
            * on associe le tresor a une case dont le numéro est supérieur a 24(qui n'est pas un coin)
#

* tri_aleatoire_cases_mouvantes(plateau)
    * creer un tableau de int de taille 34, le remplir avec 0,1,2,3,4...33
    * trier aléatoirement ce tableau
    * pour les 12 cases de types a:
        + si le num de la case est 0(la case tmp), le paramètre type de la case_tmp est ax,x étant une orientation aléatoirement choisie entre les 4, sinon:
            * pour la case dont le numéro correspond a l'indice dans le tableau d'entier: son type devient ax, x étant une orientation aléatoirement choisie entre les 4
    * pour les 6 cases de type c:
        + si le num de la case est 0(la case tmp), le paramètre type de la case_tmp est cx,x étant une orientation aléatoirement choisie entre les 4, sinon:
            * pour la case dont le numéro correspond a l'indice dans le tableau d'entier: son type devient cx, x étant une orientation aléatoirement choisie entre les 4
    * pour les case de type b:
        + si le num de la case est 0(la case tmp), le paramètre type de la case_tmp est bx,x étant une orientation aléatoirement choisie entre les 4, sinon:
            * pour la case dont le numéro correspond a l'indice dans le tableau d'entier: son type devient bx, x étant une orientation aléatoirement choisie entre les 4
#

* assignation_indices_cases(tableau de lignes)
    * en s'aidant de la position des lignes par rapport au plateau on et de maths, on parvient à assigner des indices hauteur et largeur a chaque case de telle sorte que la première case aie comme indices 0,0 et la dernière(en bas a droite) 7,7.
    * calculs non détaillés ici car conception détaillée
#

* tableau de lignes creer_lignes_mouvantes()
    * on crée un tableau de 12 lignes
    * pour chaque ligne
        + on lui assigne son numéro(de 1 a 12)(paramètre numero)
        + on créé un tableau de 8 cases et on l'assigne a la ligne
        + pour chaque case de la ligne
            * on assigne au paramètre numligne de la case le numéro de la ligne
    * on renvoie le tableau
#

* plateau creer_casesfixes()
    * on crée un plateau
    * on s'aide des indices pour creer les cases fixes du plateau en suivant le modèle(on leur assigne le bon type et la bonne place)
    * retourne le plateau
#

* void assigner_valeurs_orientations(p)
    * pour chaque case du plateau:
        + si case an alors h=b=1 et g=d=0
        + si case ae alors h=b=0 et d=g=1
        + si case as alors h=b=1 et d=g=0
        + si case ao alors h=b=0 et d=g=1
        + si case bn alors h=d=1 et b=g=0
        + si case be alors h=g=0 et b=d=1
        + si case bs alors g=b=1 et h=d=0
        + si case bo alors h=g=1 et d=b=0
        + si case cn alors g=0 et h=d=b=1
        + si case ce alors h=0 et d=g=b=1
        + si case cs alors d=0 et h=g=b=1
        + si case co alors b=0 et h=g=d=1
#

* int tresor_atteignable(plateau p, joueur j)
    * si peut_on_deplacer_ici(p, j.case, j.tresor[0].case)==1
        + retourne 1
    * sinon
        + retourne 0
#

* int est_on_sur_tresor(joueur j)
    * si j.case.tresor==j.tresorsrestants[0]
        + retourne 1
    * sinon
        + retourne 0
#

* void tresor_suivant(joueur j)
    * pour tous les tresors restants -1(j.tresorsrestants)
        + tresors[i]=tresors[i+1]
    * dernier tresor(qui est ducoup en double)='\0'
#

* void deplacer_pion(joueur j, plateau p, case c2)
    * si pion_deplacable==1
        + j.case=c2
    * sinon
        + afficher "Le pion ne peux pas être déplacé ici"
#

* int pion_deplacable(plateau p, case c1, case c2)
    * si le pion n'est pas entre 4 murs(utiliser case_compatible) ET si peut_on_deplacer_ici(p, c1, c2)==1
        + retourne 1
    * sinon
        + retourne 0
#

static int tabcaseint=0

* int peut_on_deplacer_ici(plateau p, case c1, case c2, case* tabcase)
    * tabcase[tabcaseint]=c1
    * tabcaseint++
    * (cette ligne est un for)si tabcaseint=0, pour les 4 orientation, sinon, pour seulement 3(pas celle d'ou l'on vient):
        + si case_compatible(p, c1, (la case a coté de c1(suivant l'orientation)), tabcase)==1
            * peut_on_deplacer_ici(p, la case a coté, c2, tabcase)
    * si c2 présente dans tabcase
        + retourne 1
    * sinon
        + retourne 0
#

* int case_compatible(case c1, case c2, char orientation(où est la case 1 par rapport a la 2))
    * si c1.orientation=1 et c2.orientation opposée=1
        + retourne 1
    * sinon
        + retourne 0
#

* void afficher_plateau(plateau p)
    * pour i de 0 a 7
        + afficher_fleche(s1)
    * pour i de 0 a 7
        + afficher_fleche(s2)
    * afficher_lignes(p)
    * pour i de 0 a 7
        + afficher_fleche(n1)
    * pour i de 0 a 7
        + afficher_fleche(n2)
#

* void afficher_fleche(char c)
    * si c='s1', afficher "|"
    * si c='s2', afficher "v"
    * si c='e', afficher "->"
    * si c='o', afficher "<-"
    * si c='n1', afficher "^"
    * si c='n2', afficher "|"
#

* void afficher_case_tmp(case c)
    * afficher "Case pour pousser:"
    * afficher_case(c)
#

* void afficher_lignes(plateau p)
    * pour i de 1 a 7
            * afficher_ligne(p.l[i])
#

* void afficher_ligne(ligne l)
    * afficher_fleche(e)
    * pour i de 1 a 7
        + afficher_case(l.c[i])
    * afficher_fleche(o\n)
#

* void afficher_case(case c)
    * afficher_murs(c)
    * afficher_pion(c)
    * afficher_tresor_sur_case(c)
#

* void afficher_liste_tresors(joueur j)
    * pour tous les trésors restants
        + afficher ""numéro du trésor". "nom du trésor"\n"
#

* void afficher_tresor_sur_case(case c)
    * afficher "c.tresor" 
#

* void afficher_murs(case c)
    * afficher les murs en fonction du type de c avec des "|" et "-"
#

* void afficher_pion(case c)
    * changer la couleur du pion en fonction de c.joueur
    * afficher "I" de la bonne couleur
#

* void afficher_coup(case c1, case c2, ligne l, joueur j)
    * afficher "Le joueur j.nom a poussé la ligne l et a déplacé son pion de la case c1 a la case c2"
#

* int est_elle_decalable(ligne l)
    * Si l=ligne_tmp
       + on retourne 1
    * Sinon on retourne 0
#

* void pousser_rangee(ligne l)
    * Si est_elle_decalable(l)==1
        + Pour i de 0 a 7
            * l.case[i+1]=l.case[i]
        + l.case[0]=case_tmp
        + case_tmp=case[8]
#

* ligne derniere_ligne(ligne l)
    * ligne_tmp=l
#

* void inserer_case(case c)
    * c prend la valeur de case_tmp
#

* void remplacer_case(case c)
    * case_tmp prend la valeur de c
#

* int yatil_des_pions(case c)
    * Si il y a 0 joueurs sur la case:
        + on renvoit 0
    * Sinon:
        + on renvoit 1
#

# Structures

* plateau
    * les 12 lignes
    * la case temporaire
#

* joueur
    * le nom
    * la couleur
    * si c'est une ia(un int)
    * la liste des tresors qu'il lui reste a atteindre
#

* tresor
    * le nom
    * son numero
    * la case où il est
#

* ligne
    * le numéro de la ligne
    * le tableau de cases de la ligne
#

* case
    * le trésor sur la case(rien si il n'y en a pas)
    * le types de case et son orientation(chaine(an, be...))
    * si il y a des murs au 4 orientations(4 entiers(booléens) h, b, d, g)
    * le pion sur la case (PERSONNE si il n'y en a pas)
    * numero_ligne le numéro de la ligne auquelle la case appartient (tableau de 3 int, -1, -1, -1 si case non mouvante)
    * numero le numéro de case/34
    * les indices de la case dans le plateau
#
