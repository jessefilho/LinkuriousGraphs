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
A quoi ressemble ce graphe ? Dessiner le grossièrement. Comment qualifie-t-on ce type de graphe ?
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

Question 8. Compléter la fonction JavaScript `getNeighbours()’ utilisé dans ’selectNode()' pour
afficher des informations sur un nœud dans le panneau `nodeTabContent' de droite. Les informations
à afficher sont les vignettes des voisins du nœud courant. Un clic sur une de ces vignettes correspond
à la sélection d'un nouveau nœud d'intérêt, et donc à la mise à jour dans le graphe et dans l'onglet
`Current node'.

Question 9. Nous souhaitons étudier les héros les plus "importants". Pour ce faire, on choisit de ne
garder que les héros qui ont de nombreuses connexions (arcs de poids supérieur ou égal à 50). Ecrire
le pseudocode de l'algorithme qui effectuerait ce premier filtrage des arcs.
