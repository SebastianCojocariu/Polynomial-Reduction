Sebastian Cojocariu 321CB UPB ACS
                                                       
                                                       Polynomial reduction

Fie k numarul de culori disponibile,carora le vom asigna,formal,valorile 0,1,...,k-1
   Pentru fiecare nod v din graf,notam cu p_v(i),cu i=0,k valoarea de adevar a propozitiei "nodul v are culoarea i"(valoarea care va fi convertita la 1 cand e True,respectiv 0 pentru False).Evident,
vom avea k*|V| astfel de variabile(cate k culori pentru fiecare nod,care sunt in numar de |V|);

Transformarea grafului primit ca input in SAT va fi alcatuita din 3 tipuri de clauze:

1)Pentru fiecare nod g, avem clauza:   p_v(0) V p_v(1) V...V p_v(k-1) -care va fi true doar daca
macar un literal este 1,deci nodul g a fost colorat cu cel putin o culoare.
   Sunt |V| astfel de clauze,fiecare cu cate k literali,deci |V| clauze cu cate k variabile fiecare.

2)Pentru fiecare nod g, avem clauzele de tipul: (~p_v(i) V ~p_v[j]),(i=0,k-1 ; j=i+1,k-1) care va fi true doar daca p_v(i) si p_v(j) nu sunt ambele true,adica nodul v a fost colorat cu cel mult o culoare dintre i si j(iar atunci cand i,j parcurg toate culorile,avem garantia ca exista exact o culoare folosita pentru nodul g).Pentru fiecare nod g avem O(k^2/2) clauze,fiecare cu cate 2 variabile,deci in total avem O(|V|*k^2) clauze si tot atat de multi literali(de aceeasi complexitate)

3)Pentru fiecare muchie (u,v) din graf,definim clauzele de tipul: (~p_u(i) V ~p_v(i)),cu i=0,k-1 .Fiecare dintre aceste clauze sunt True <=> u,v nu au fost amandoua coloare in acelasi timp
cu culoarea i (i=0,k-1),adica fiecare muchie are nodurile de culori diferite.Daca notam cu E multimea muchiilor grafului,obtinem k*|E| clauze,respectiv 2*k*|E| variabile

Transformarea este alcatuita din toate tipurile de clauze enumerate mai sus,pentru fiecare nod g din graf.

Observam ca fiecare clauza are cel mult k literali.Intrucat obtinem O(|V|)+O(|V|*k^2)+O(k*|E|),iar |E|<=|V|*(|V|-1)/2 clauze,conchidem ca transformarea e polinomiala in raport cu numarul de noduri ale grafului initial.
