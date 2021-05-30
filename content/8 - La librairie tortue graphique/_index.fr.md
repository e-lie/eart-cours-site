---
title: 6 - La librairie tortue graphique
weight: 4
draft: no
---


## Librairies Python

Une librairie (ou module) est un **ensemble de fonctions**:

- spécialisées pour un usage
- qui sont rangées dans un module
- qu'on peut importer dans un programme

Par exemple la librairie `PIL` que nous avons utilisée dans le cours sur les images numériques permet d'ouvrir des fichiers images avec la fonction `img.load()`. On ajoute toujours des parenthèses `()` à la fin du nom d'un fonction pour dire que c'est une fonction. Nous verrons les fonctions plus en détails dans le cours suivant.


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

**Exercice:** changer le nom de la tortue en lucie et faite la reculer de 100 avec la fonction `backward()`

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

**Exercices:**:

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

```
import turtle 

spiral = turtle.Turtle()

for i in range(20):
    spiral.forward(i * 10)
    spiral.right(144)
    
turtle.done()
```

Notice that now I’m moving the turtle forward by a different amount each time. What happens if instead of multiplying i by 10, I multiply it against itself? What if I do spiral.forward(i * i) instead?

Essayez


### Example 6: Changing line color

```python
import turtle 

painter = turtle.Turtle()

painter.pencolor("blue")

for i in range(50):
    painter.forward(50)
    painter.left(123) # Let's go counterclockwise this time 
    
painter.pencolor("red")
for i in range(50):
    painter.forward(100)
    painter.left(123)
    
turtle.done()
```


What if you want different colors? You could always try and guess what colors the turtle module can support, but if you want to be precise, you can use this colorpicker instead.

At the top of the screen, the website will provide a ‘#’ mark and a sequence of 6 letters or numbers that represents the color. The turtle module will accept colors in this format.

```python
import turtle 

painter2 = turtle.Turtle()

painter2.pencolor(0,0,250)
painter2.forward(30)

painter2.pencolor(250,0,0)
painter2.forward(30)
```

### Example 7: Variables

One of the powerful things about computers and programming is that they can do work humans would find boring. For example, what if we wanted to draw a hexagon (shape with 6 sides)? By how many degrees should we turn each time? What if we want a shape with 15 sides?

Rather then computing the number each time ourselves, we can instead define variables and have Python use a formula to find out for us.

Here, we’ve set the number of sides to be 6, and the side length to be 70. What happens if we change the variables?
Code

```python
import turtle 

polygon = turtle.Turtle()

num_sides = 6
side_length = 70
angle = 360.0 / num_sides 

for i in range(num_sides):
    polygon.forward(side_length)
    polygon.right(angle)
    
turtle.done()
```

Expected Output

Additional notes

Something that confuses many beginners is the = symbol. In Math, whenever we see A = B, we know that A and B must be identical – in Math, = means “equality”.

However, = means something a little different in programming. When we see A = B, it means that whatever A is will now be set equal to B – in programming, = means “assignment”.

So, if we see the following code:

my_variable = 3 + 4 
print(my_variable)

my_variable = my_variable + 5
print(my_variable)

…the output will be 7 and 12. We always computer whatever is on the right side, then change the variable on the left side to that value.


### Example 7: Nested loops

This will make a matrix of dots 5 dots wide and 7 dots high. Try experimenting with the variables at the top to change the number of dots and the distance between them.

The for loop on the very inside (for i in range(width):) draws a single line of dots. The code then causes the turtle to move back, then move down a row.

```python
import turtle 

seurat = turtle.Turtle()

dot_distance = 25
width = 5
height = 7

seurat.penup()

for y in range(height):
    for i in range(width):
        seurat.dot()
        seurat.forward(dot_distance)
    seurat.backward(dot_distance * width)
    seurat.right(90)
    seurat.forward(dot_distance)
    seurat.left(90)
    
turtle.done()
```

### Example 8: Jumping around and changing speed

`turtle.setposition(x, y)` will set the turtle’s position to the coordinates you plug in. (0, 0) is located at the center of the screen – where the turtle first started. Note that you need to make sure the turtle’s pen is up, otherwise it’ll draw a line back to that.

You can change the speed of the turtle by doing turtle.speed(number). If you set the speed to 10, the turtle will go really fast. If you set the speed to 1, the turtle will go really slow (which is useful for trying to understand how some complicated thing is being drawn). If you set the speed to zero, however, the turtle will go at warpspeed and will draw as fast as it can.

The speed cannot be lesser then 0 or greater then 10.
Code

```python
import turtle 

ninja = turtle.Turtle()

ninja.speed(10)

for i in range(180):
    ninja.forward(100)
    ninja.right(30)
    ninja.forward(20)
    ninja.left(60)
    ninja.forward(50)
    ninja.right(30)
    
    ninja.penup()
    ninja.setposition(0, 0)
    ninja.pendown()
    
    ninja.right(2)
    
turtle.done()
```

