* int yatil_des_pions(case c)
    * Si il y a 0 joueurs sur la case:
        + on renvoit 0
    * Sinon:
        + on renvoit 1
#

* void remplacer_case(case c)
    * case_tmp prend la valeur de c

* void inserer_case(case c)
    * c prend la valeur de case_tmp
#

* int decalee_avant(ligne l, int sens)
    * Si l == a ligne_tmp ET si sens+sens_tmp égal à 0
         + on retourne 1
    * Sinon on retourne 0
#

* int est_elle_decalable(ligne l, int sens)
    * Si decalee_avant(l, sens)==1 alors
       + on retourne 0
    * Sinon on retourne 1
#

* int peut_on_pousser(ligne l, int sens)
    * Si est_elle_decalable(l, sens)==1 ET si l.decalable=1
        + on retourne 1
    * Sinon on retourne 0
#

* void pousser_rangee(ligne l, int sens)
    * Si peut_on_pousser(l, sens)==1
        + Si sens négatif
        + Pour i de 1 a 9
