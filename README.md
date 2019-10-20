MUGEN: Marvel Universe Graph Exploration
--


About the students:

Jean-Yves RAMEL, Professeur.

Jesse Ferreira, Student.
21805893
jessefilhojfnf@gmail.com


About MUGEN
MUGEN is a web platform skeleton to visualise and abalyze graphs It has been 
initialy developed by Frédéric RAYAR in the context of the "Graphs and their applications" course.

This course takes place in the Polytech'Tours engineering school (University of Tours)



--

TP Questions
--

Question 1. Si on considère un graphe G pour lequel :
1. les nœuds sont les personnages et les comics
2. les arêtes sont les liens (personnage, comic)

A quoi ressemble ce graphe ? Dessiner le grossièrement. Comment 
qualifie-t-on ce type de graphe ?
Comment transformer G pour créer un graphe type ‘réseau social' à partir de ce jeu de données ?
Appelons ce nouveau graphe G*, quel poids peut-on associer aux arêtes ?


Question 2. Par défaut, le site charge le graphe `xxxxxxxx.json'. Modifier `mugen.js' pour que le
graphe chargé par défaut soit le graphe stocké dans le fichier mu_128.json. 

Question 3. Dans `help.html', compléter la section `About the students'. Rajouter au minimum vos
noms, prénoms, numéros étudiant.


Question 4. Dans index.html, associer comme évènement sur le bouton "fl (img au pdf)" la méthode JavaScript
`flLayout()' qui est déjà implémentée.

Question 5. Compléter la fonction JavaScript `changeNodeStyles()' qui change la forme et la couleur
de tous les noeuds (type= "circle" et color="#000"). Cette fonction est associée au bouton .


Question 6. Compléter la fonction JavaScript `showHideEdges()' qui permet d'afficher ou non les
arêtes. Cette fonction est associée au bouton . 
Quel peut-être l'intérêt d'une telle fonctionnalité ?

R: Allow a reorganazetion of nodes with a low complex
Removing an edge takes O(1) time

Question 8. Compléter la fonction JavaScript "getNeighbours()" utilisé dans ’selectNode()' pour
afficher des informations sur un nœud dans le panneau "nodeTabContent" de droite. Les informations
à afficher sont les vignettes des voisins du nœud courant. Un clic sur une de ces vignettes correspond
à la sélection d'un nouveau nœud d'intérêt, et donc à la mise à jour dans le graphe et dans l'onglet
`Current node'.

Question 9. Nous souhaitons étudier les héros les plus "importants". Pour ce faire, on choisit de ne
garder que les héros qui ont de nombreuses connexions (arcs de poids supérieur ou égal à 50). Ecrire
le pseudocode de l'algorithme qui effectuerait ce premier filtrage des arcs.

```
pop_heros = []

foreach pop_hero in edges:
    if pop_hero.weight >= 50:
        popularity = sum of unique weights of pop_hero unique 
        pop_heros.push({ pop_hero, popularity })
     
return sortedDesc(pop_heros)
```

Question 10. Pour filtrer le graphe, écrire la fonction JavaScript pruneGraph()' qui supprime les arêtes
dont le poids est inferieur a un paramètre global 'MIN_EDGE_WEIGHT. Faire appel à cette fonction
dans la méthode `on load()' avant l'affichage du graphe.
Aide : (Suppression d’arc = sig.graph.dropEdge(edge.id);)

Question 11. Avec MIN EDGE WEIGHT = 50, lancer l'algorithme de dessin de graphe FruchtermanReingold. Que remarquez-vous ? Compléter la fonction `pruneGraph()' pour éventuellement supprimer
les éléments en trop".

```
Il a y encore des noudes que, empêche d'avoir une visualisation propre de ces qui sont plus 
important.
```

Question 12. Regarder et expliquer la fonction JavaScript `hitsAlgorithm()' qui fait appel a
l'algorithme HITS 1, déjà implémente. Qui sont, dans l'ordre, les 5 personnages les plus importants,
selon le critère HITS ?
Aide : https://en.wikipedia.org/wiki/HITS_algorithm

This function will fetch by the authorities nodes checking the hits of each nodes. 
The objetive is find the most relevant nodes. Then list of autorithies is sorted to give
the colour to the top select nodes.

```
HITS 0 : CAPTAIN AMERICA 
HITS 1 : HAWK  
HITS 2 : ANT-MAN/DR. HENRY J.  
HITS 3 : THING/BENJAMIN J. GR  
HITS 4 : HULK/DR. ROBERT BRUC
```
Question 13. En vous basant sur l’algorithme précèdent, compléter la fonction JavaScript
`highestDegreeNodes()' qui colorie en rouge les personnages qui ont le plus de liens. Le reste des
nœuds sera colorie en noir. Qui sont, dans l'ordre, les 10 personnages les plus importants, selon le
critère des degrés élevés ?

```
HITS 1 : CAPTAIN AMERICA  mugen.js:780:3
HITS 2 : HAWK  mugen.js:780:3
HITS 3 : ANT-MAN/DR. HENRY J.  mugen.js:780:3
HITS 4 : THING/BENJAMIN J. GR  mugen.js:780:3
HITS 5 : HULK/DR. ROBERT BRUC  mugen.js:780:3
HITS 6 : QUICKSILVER/PIETRO M  mugen.js:780:3
HITS 7 : HUMAN TORCH/JOHNNY S  mugen.js:780:3
HITS 8 : WONDER MAN/SIMON WIL  mugen.js:780:3
HITS 9 : MR. FANTASTIC/REED R  mugen.js:780:3
HITS 10 : IRON MAN/TONY STARK
```

Question 14. Regarder et expliquer (partie 1 et partie 2) la fonction JavaScript `louvainClustering()'
qui fait appel à l'algorithme de Louvain, déjà implémenté.
Aide : https://github.com/Linkurious/linkurious.js/tree/linkurious-version/plugins/sigma.statistics.louvain

```

Part 1:
Les colour des noudes sont attribué en basant sur les classes de chaque noudes qui est 
generé par l'index calculé methode statistc du louvain.


Part 2:
repartions sont ordenées et mapped dans l'order croissante

donc l'algorithme de Louvain reorganise les graphs en basant sur le clustering
hierarchique, en regroupant les noudes voisins en communautées. 
```
Question 15. Proposer le pseudo-code d’un algorithme et d’une signature de nœuds qui permettrait de
mesurer une similarité ou dissimilarité entre 2 nœuds dans le graphe. Justifier et expliquer l’intérêt
d’une telle fonction. 



```
à un moment donné peut etre exister deux graphes \(G_1(N_a,E_a)\) et \(G_2(N_b,E_b)\) 
avec éventuellement un nombre différent de nœuds et d'arêtes, et il peuvent avoir des 
correspondance entre graph, c'est-à-dire, avoir la même quantité de noudes voisins, dont 
les voisins aussi peuvent avoir les mêmes nombre des proichain voisins et etc. Donc, 
pour mesure la similarité on peut comparer les ensemble de voisin de chaque G (\(G_1\) et 
\(G_2\) ), par contre, ça peut deviens coute.

L'intéret en cet type de analysis est que on peut trouve de heros que peut avoir de memes amis
et aussi enimis, et donc ils peuvent etre uni por sauve la vie humane de Thanos, comme dans 
le film "Avengers: Endgame".

voisans1 = getNeighbours(sig_GA, nodeId_GA)
voisans2 = getNeighbours(sig_GB, nodeId_GB)

for i in voisans1.nodes:
    for j in voisans2.nodes:
    
        if i != j
            dissimilarity_flag = 0
        else 
            similarity_flag = 1

```

Question 16. Proposer le pseudo-code d’un algorithme qui permettrait de mesurer une similarité ou
dissimilarité entre 2 sous-graphes en renvoyant éventuellement aussi un appariement (matching)
entre les éléments des 2 sous-graphes. Justifier et expliquer l’intérêt d’une telle fonction. 
```
Là l'ideé est un peu pareil à cela sur la dernier question, mais là on cherche les 
communauté que se rasenssembles à la fois de concentré de l'analyse sur chaque individuos, 
maintenant on cherchee le similarité de sub-graph. On peut faire cela aprés le partition hierarchique, 
et donc, parcourir les enssemble de sub-graph en demandant et comparant les labels.

L'intéret en cet type de analysis est de trouver de mêmes caracteristques entre des communautes.


for i in graphA.nodes:
    for j in graphB.nodes:
    
        if node[i]._louvain != node[j]._louvain
            dissimilarity_flag = 0
        else 
            similarity_flag = 1
        

```

Question 17. Regarder et expliquer la fonction JavaScript `computeDensities()' qui calcule les densités
intra- et inter-cluster d'un partitionnement donnée. Indiquer les expressions mathématiques des
différentes valeurs intéressantes calculées par l’algorithmes. Quelles valeurs obtient-on pour le
partitionnement avec l'algorithme de Louvain ?
```
Aprés la repartions de communautées, l'algorithme va mesures les poids  entre 
noudes de une communautées et entre communautées. Oú le densité intra-cluster c'est le
nombre de arcs interne à une communautées par quantite de possibles noudes, dont
de global internal_density sera la moyenne entre les repartions. Et inter-cluster c'est
la maximum distance entre les communautées.

intra-cluster = ( Sum des |E| / |V| * |V| - 1 ) / nb repartions total
inter-cluster = |E| - |External E| /  (|V| * |V| - 1) - quantite total de possibles noudes

Nb internal edges = 80  
Internal density = 0.25774198568316214  
External density = 0.0016790597265531303

```
