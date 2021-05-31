---
title: 8 - La librairie tortue graphique
weight: 2
draft: no
---

## La tortue graphique et la librairie `turtle`

La tortue graphique est une principe inventé par le créateur du langage Logo qui est destiné à l'apprentissage de la programmation à l'école. Il s'agit de se familiariser avec la logique du code, les conditions (if) et boucles (for) que nous avons déja vu, à l'aide du **dessin**.

La tortue est une sorte de crayon virtuel auquel on donne des ordres pour se déplacer et qui dessine des lignes en se déplaçant.

La librairie (ou module) Python qui permet d'utiliser la tortue graphique s'appelle `turle`.

Avant de pouvoir dessiner une ligne avec `turtle` il y a donc 4 étapes:

1. Importer le module avec le code `import turtle`. Si on saute cette étape il est impossible de créer une tortue pour dessiner et les fonctions seront inaccessibles.
2. Créer une tortue (on dit **un objet** tortue en programmation) et la ranger dans une variables (c'est à dire lui coller une étiquette avec son nom):

```python
lucie = turtle.Turtle()
```

ma tortue s'appelle Lucie mais on peut lui donner le nom qu'on veut (c'est une variable)

3. Dessiner des choses, faire des trucs à volonté.
4. Lancez la fonction `turtle.done()` à la fin pour finir le dessin

`turtle.done()` met le programme en pause.  Il faut fermer la fenêtre de dessin pour continuer l'exécution du programme.

### Exemple 1: dessiner une ligne

```python
import turtle
bob = turtle.Turtle()
bob.forward(50)
turtle.done()
```

##### Exercice:

1. changer le nom de la tortue en lucie
1. faite la reculer de 100 avec la fonction `backward()`

### Exemple 2: dessiner un carré.

Un seule ligne c'est un peu limité et ennuyeux. On peut tourner la tortue d'un angle précis pour dessiner des figures plus intéressantes.

```python
import turtle

silly = turtle.Turtle()

silly.forward(50)
silly.right(90)  # 90 degrés signifie un angle droit

silly.forward(50)
silly.right(90)

silly.forward(50)
silly.right(90)

silly.forward(50)
silly.right(90)

turtle.done()
```
Essayez ce programme

#### Rappel sur les angles

Lorsqu'on veux décrire un angle en degré il faut simplement se rappeler qu'un tour complet c'est 360 degrés.

- Un angle droit c'est `360/4 = 90` degrés comme pour le carré précédent
- Un tier de tour c'est `360/3 = 120` degrés
- Demi tour c'est donc `360/2 = 180` degrés

la fonction `right(angle)` permet de tourner à droite en remplaçant `angle` par un nombre de degrés.

Pour tourner dans l'autre sens on utilise la fonction `left(angle)`.

##### Exercices:

1. Modifier le programme précédent pour dessiner le carré avec seulement les fonction `left()` et `backward()`
2. Dessinez un triangle : quel angle faut-il utiliser ?

### Exemple 3: Dessiner un carré avec un boucle

Un autre aspect limité et ennuyeux de nos programmes précédent c'est de devoir copier-coller le code. Il serait plus adapté de demander à Python de répéter le code pour nous avec une boucle `for` comme nous avons vu durant les cours précédents.

```python
import turtle 

smart = turtle.Turtle()

for i in range(4):
    smart.forward(50)
    smart.right(90)
    

turtle.done()
```

### Exemple 4: Dessiner une étoile

```python
import turtle 

star = turtle.Turtle()

for i in range(50):
    star.forward(50)
    star.right(144)
    
turtle.done()
```

Pourquoi avons nous choisi le nombre “144”? Pourquoi est-ce important ? Que se passerait-il si nous choisissions un autre nombre ?

### Exemple 5: Étoile en spirale

```python
import turtle 

spiral = turtle.Turtle()

for i in range(20):
    spiral.forward(i * 10)
    spiral.right(144)
    
turtle.done()
```

Remarquez que dans ce programme la tortue avance d'un nombre de pixel différente à chaque fois. Que se passerai-t-il si plutôt que de multiplier i par 10 on le multipliait par lui même (i*i) ?

- Essayez `i*i` à la place de `i*10`
- Essayer avec `i*10` comme précédemment mais en **augmentant le nombre de tours** pour faire une étoile plus grande

### Example 6: Changer les couleurs

```python
import turtle 

lucie = turtle.Turtle()

lucie.pencolor("blue")

for i in range(50):
    lucie.forward(50)
    lucie.left(123)
    
lucie.pencolor("red")
for i in range(50):
    lucie.forward(100)
    lucie.left(123)
    
turtle.done()
```

Que faire si nous voulons changer de couleur ? Il existe une fonction `pencolor()` pour changer la couleur de la tortue (du crayon).

Pour désigner une couleur on peut soit utiliser son nom en anglais `"red"`, `"white"` etc ou sa quantité de rouge, vert et bleu avec des nombres comme nous avons vus dans le cours 7 sur les images numériques.

![](../../../../images/eart/220px-RGB_sliders.svg.png)
![](../../../../images/eart/220px-AdditiveColor.svg.png)
![](../../../../images/eart/rgb-examples.png)


Par exemple:

```python
import turtle 

lucie = turtle.Turtle()

lucie.pencolor(0,0,250)
lucie.forward(30)

lucie.pencolor(250,0,0)
lucie.forward(30)
```

##### Exercices:

1. Utilisez un outil en ligne (colorpicker) pour trouver comment code la couleur **cyan foncé**: vous pouvez utiliser le site http://www.colorpicker.com/
2. Il existe aussi une fonction pour changer la couleur du fond (background color). Essayer de la chercher dans la documentation officielle https://docs.python.org/zh-cn/3/library/turtle.html (en Chinois ici). Il est très important de pouvoir lire un peu les documentations pour découvrir de nouvelles fonctions même si c'est assez incompréhensible et effrayant au départ.
3. Utilisez une boucle pour faire une étoile comme dans l'exemple 5 précédent mais en utilisant 20 nuances de vert de plus en plus clair (indice utilisez la variable i pour changer la quantité de vert).
4. Essayez de dessiner sur un fond noir maintenant.

### Example 7: Variables

L'un des atouts des ordinateurs et de la programmation est qu'ils peuvent effectuer des tâches que les humains trouveraient ennuyeuses. Par exemple, si nous voulions dessiner un hexagone (forme à 6 côtés) ? De combien de degrés devons-nous tourner à chaque fois ? Et si nous voulions une forme à 15 côtés ?

Plutôt que de calculer nous-mêmes le nombre à chaque fois, nous pouvons définir des variables et demander à Python d'utiliser une formule pour le trouver à notre place.

Ici, nous avons fixé le nombre de côtés à 6 et la longueur des côtés à 70. Que se passe-t-il si nous changeons les variables ?


```python
import turtle 

lucie = turtle.Turtle()

nombre_de_cotes = 6
longueur_cote = 70
angle = 360.0 / nombre_de_cotes 

for i in range(nombre_de_cotes):
    lucie.forward(longueur_cote)
    lucie.right(angle)
    
turtle.done()
```

##### Exercices:

1. Utilisez une variable pour stocker une couleur par exemple `rouge = (255, 0, 0)`
2. Utilisez `pencolor` avec votre variable pour changer la couleur du crayon
3. Créez une palette de couleur avec une variable et une liste par exemple `ma_palette_rvb = [ (150, 0, 0), (0, 150, 0), (0, 0, 150) ]` ou `ma_palette = ["red", "yellow", "purple"]`
4. Utilisez cette palette pour changer la couleur à chaque côté du polygone (indice il faut utiliser `pencolor(ma_palette[i % len(ma_palette)]))`) nous allons expliquer pourquoi.


### Exemple 7: Boucles imbriquées

Cela donnera une matrice de points de 5 points de large et de 7 points de haut. Essayez d'expérimenter avec les variables en haut pour changer le nombre de points et la distance entre eux.

La boucle `for` à l'intérieur (`for i in range(width):`) dessine une seule ligne de points. Le code fait ensuite reculer la tortue, puis la fait descendre d'une ligne.

```python
import turtle 

lucie = turtle.Turtle()

dot_distance = 25
width = 5
height = 7

lucie.penup()

for y in range(height):
    for i in range(width):
        lucie.dot()
        lucie.forward(dot_distance)
    lucie.backward(dot_distance * width)
    lucie.right(90)
    lucie.forward(dot_distance)
    lucie.left(90)
    
turtle.done()
```

##### Exercices:

1. modifiez le code précédent pour avoir un couleur différente à chaque ligne
2. modifiez le code pour avoir une couleur différente à chaque colonne (mais le même groupe de couleur sur chaque ligne)

### Exemple 8: Changer la vitesse et faire sauter le crayon à une position définie

La fonction `turtle.setposition(x, y)` fixera la position de la tortue aux coordonnées que vous avez introduites. (0, 0) est situé au centre de l'écran - là où la tortue a commencé. Notez que vous devez vous assurer que le stylo de la tortue est en haut (`penup()`), sinon elle tracera une ligne vers ce point.

Vous pouvez modifier la vitesse de la tortue en faisant `turtle.speed(number)`. Si vous fixez la vitesse à 10, la tortue ira très vite. Si vous fixez la vitesse à 1, la tortue ira très lentement (ce qui est utile pour essayer de comprendre comment une chose compliquée est dessinée). Si vous mettez la vitesse à zéro, la tortue ira à la vitesse de la lune et dessinera aussi vite qu'elle le peut.

La vitesse ne peut pas être inférieure à 0 ou supérieure à 10.

```python
import turtle 

ninja_turtle = turtle.Turtle()

ninja_turtle.speed(10)

for i in range(180):
    ninja_turtle.forward(100)
    ninja_turtle.right(30)
    ninja_turtle.forward(20)
    ninja_turtle.left(60)
    ninja_turtle.forward(50)
    ninja_turtle.right(30)
    
    ninja_turtle.penup()
    ninja_turtle.setposition(0, 0)
    ninja_turtle.pendown()
    
    ninja_turtle.right(2)
    
turtle.done()
```

##### Exercices:

1. Mettez la vitesse à 1 et essayez de bien comprendre comment marche ce dessin
2. Essayez de modifier le code pour dessiner une étoile à 8 branches/traits seulement
3. Maintenant que nous savons lever le crayon, dessinez deux étoiles identiques l'une à côté de l'autre.

