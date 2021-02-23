* 

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

* void afficher_lignes_mouvantes(ligne* l)
    * pour i de 1 a 7
        + si i modulo 2 =0
            * afficher_ligne(l[i])
        + Sinon
        + pour j de 1 a 7
            * si j modulo 2 =0
                * afficher_case(case numéro i de la ligne j+6)
#

* void afficher_ligne(ligne l)
    * pour i de 1 a 7
        + afficher_case(l.c[i])
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
