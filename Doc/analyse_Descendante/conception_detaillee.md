# Fonctions:

* joueur* entrer_joueurs()
    * joueur *j= demander_nombre_joueurs()
    * demander_joueurs_humains(j)
    * demander_couleur_joueurs(j)
    * demander_pseudo_joueur(j)

* void demander_joueurs_humains(joueur *j)
    * afficher "Combien d'IA?"
    * si nombre d'IA  supérieur a nbrdejoueur-1
        + afficher "Nombre d'IA pas cohérent avec le nombre de joueurs"
    * sinon 
        + pour i de 1 a nombre d'IA
            * j[i].ia=1
#

* joueur* demander_nombre_joueurs()
    * afficher "Combien de joueurs sur cette partie?"(nbr)
    * si nbr différent de 2 3 et 4
        + créer des struct joueurs en conséquence
    * sinon
        + afficher "Il n'y a pas un nombre adéquat de joueur"
#


* void demander_couleur_joueurs(joueurs *j)
    * pour chaque joueur
        + afficher "Quelle est la couleur du joueur j.i?"
        + j.couleur= le scanf 
#

* void demander_pseudo_joueur(joueur *j)
    * pour chaque joueur
        + afficher "Quel est le pseudo du joueur j.i?"
        + j.nom= le scanf
#

* void changer_couleur(joueur j)
    * # ???????
#

* joueur creer_ia(joueur j)
    * j.ia=1
#

* void victoire_dun_joueur(joueur j)
    * si case_depart(j)==1
        + afficher_message_victoire(j)
        + on sort de la boucle du main avec les jouer_tour
#

* void afficher_message_victoire(joueur j)
    * afficher "Le joueur j.nom a remporté la partie!"
#

* int case_depart(joueur j)
    * si j.tresors[0]='\0'
        + retourne 1
    * sinon
        + retourne 0
#

* void jouer_tour(joueur j)
    * # ??????????

* ligne choisir_ligne_ia(plateau p, joueur j)
    * # ??????????
#

* plateau creer_plateau()
    * 
#

* assigner_valeurs_orientations(p)
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
    * afficher "Le joueur j a poussé la ligne l et a déplacé son pion de la case c1 a la case c2"
#

* int peut_on_pousser(ligne l, int sens)
    * Si est_elle_decalable(l, sens)==1 ET si l.decalable=1
        + on retourne 1
    * Sinon on retourne 0
#

* int est_elle_decalable(ligne l, int sens)
    * Si decalee_avant(l, sens)==1 alors
       + on retourne 0
    * Sinon on retourne 1
#

* int decalee_avant(ligne l, int sens)
    * Si l == a ligne_tmp ET si sens+sens_tmp égal à 0
         + on retourne 1
    * Sinon on retourne 0
#

* void pousser_rangee(ligne l, int sens)
    * Si peut_on_pousser(l, sens)==1
        + Si sens négatif
        + Pour i de 8 a 1
            * l.case[i]=l.case[i-1]
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
#

* joueur
    * le nom
    * la couleur
    * si c'est une ia(un int)
    * la liste des tresors qu'il lui reste a atteindre
#

* tresor
    * le nom
    * la case où il est
#

* ligne
    * le numéro de la ligne
    * le tableau de cases de la ligne
#

* case
    * le trésor sur la case(RIEN si il n'y en a pas)
    * le types de case et son orientation(chaine(an, be...))
    * si il y a des murs au 4 orientations(4 entiers(booléens) h, b, d, g)
    * le pion sur la case (PERSONNE si il n'y en a pas)
#
