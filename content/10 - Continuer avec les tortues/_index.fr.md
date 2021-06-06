---
title: 10 - Continuer avec les tortues et des fonctions
weight: 4
draft: no
---

### Exemple 1: fonction de carré

```python
import turtle 

def carre(longueur_cote):
    smart = turtle.Turtle()
    for i in range(4):
        smart.forward(longueur_cote)
        smart.right(90)

carre(50)
carre(100)

turtle.done()
```

#### Exercice:

- avec une boucle for dessinez 17 carrés de tailles 10, 20 jusqu'à 170.

<!-- {{%expand "correction" %}}
```python
import turtle 

def carre(longueur_cote):
    smart = turtle.Turtle()
    for i in range(4):
        smart.forward(longueur_cote)
        smart.right(90)

for i in range(17):
    carre((i+1)*10)

turtle.done()
```
{{% /expand%}} -->

### Exemple 2 : faire une fonction à partir d'instructions de dessin: le polygone

Reprenons l'exemple 7 simple du polygone comme ci-dessous:

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

Nous avons déjà deux paramètres pour le dessin de notre polygone :

1. `nombre_de_cotes` qui permet de définir le nombre de côté et donc le type du polygone
2. `longueur_cote` qui permet de choisir la taille du polygone

Remarque : la variable `angle` est une variable mais ce n'est pas un paramètre de la fonction car elle est calculée à partir des autres variables (on a pas besoin de la préciser en utilisant la fonction)

#### Exercices:

- écrire une fonction `polygone(nombre_de_cotes, longueur_cote)` qui permet de dessiner facilement des polygones d'une forme et d'une taille donnés en paramètres.

- comme dans l'exemple 1, écrivez une boucle pour dessiner tous les polygones entre 3 et 9 cotes.

<!-- {{%expand "correction" %}}
```python
import turtle 

lucie = turtle.Turtle()

def polygone(nombre_de_cotes, longueur_cote):
    angle = 360.0 / nombre_de_cotes
    for i in range(nombre_de_cotes):
        lucie.forward(longueur_cote)
        lucie.right(angle)
    
for j in range(3,10):
    polygone(j, 100)
    
turtle.done()
```
{{% /expand%}} -->

### Exemple 3: fonction d'étoile multicolore aléatoire

```python
import turtle

myscreen = turtle.getscreen()
myscreen.colormode(255)

def etoile(position, longueur_cote, couleur_crayon, taille_crayon):
    spiral = turtle.Turtle()
    spiral.pencolor(couleur_crayon)
    spiral.pensize(taille_crayon)
    spirale.penup()
    spiral.setposition(position)
    spirale.pendown()
    for i in range(20):
        spiral.forward(i * longueur_cote)
        spiral.right(144)

etoile(10, (100, 200, 255), 2)
etoile(30, (200, 200, 0), 5)

turtle.done()
```

Une des caractéristique importante des ordinateur c'est qu'ils sont capable de générer des processus aléatoires à partir de nombres aléatoire générés par une fonction `random()`.

La fonction random viens d'un librairie et doit être importée avec l'instruction `from random import random`.

Ensuite cette fonction `random()` génère un nombre à virgule entre `0` et `1.0`

Essayez par exemple le programme suivant pour voir son fonctionnement`

```python
from random import random

for iteration in range(5):
    print(random())

for iteration in range(3):
    print(random()*100)

for iteration in range(3)
    print(int(random()*100))
```

Comme dans l'exemple précédent, pour générer un nombre entier entre 0 et un certain nombre:

- on multiplie `random()` par le nombre maximum + 1
- puis on transforme le résultat en nombre entier avec `int()`

Exemple `int(random()*5)` génère un entier entre 0 et 5 et 

#### Exercices:

- générer un nombre entier entre 0 et 9 et affichez le avec `print()`

<!-- {{%expand "correction" %}}
```python
from random import random

print(int(random()*10))
```
{{% /expand%}} -->

La fonction random peut avoir plein d'utilitées. Par exemple on peut écrire une fonction pour générer une couleur de dessin aléatoire.


- écrire une fonction `couleur_aleatoire()` qui choisi une couleur aléatoire en générant aléatoirement le rouge, le vert et le bleu entre 0 et 255 avec random. enregistrez les trois couleurs dans trois variables `rouge`, `vert` et `bleu`.

- Utilisez `return (rouge, vert, bleu)` à la fin de la fonction pour qu'elle puisse retourner la couleur.

- Utilisez cette fonction pour dessiner deux étoiles de couleur aléatoire avec la fonction `etoile()` de l'exemple précédent.

<!-- 
{{%expand "correction" %}}
```python
import turtle
from random import random

myscreen = turtle.getscreen()
myscreen.colormode(255)

def couleur_aleatoire():
    rouge = int(random()*256)
    vert = int(random()*256)
    bleu = int(random()*256)
    return (rouge, vert, bleu)

def etoile(position, longueur_cote, couleur_crayon, taille_crayon):
    spiral = turtle.Turtle()
    spiral.pencolor(couleur_crayon)
    spiral.pensize(taille_crayon)
    spirale.penup()
    spiral.setposition(position)
    spirale.pendown()
    for i in range(20):
        spiral.forward(i * longueur_cote)
        spiral.right(144)

etoile(10, couleur_aleatoire(), 2)
etoile(30, couleur_aleatoire(), 5)

turtle.done()
```
{{% /expand%}} -->

### Exemple 4: Herbes partie 1, dessiner quelques herbes avec une fonction

```python
import turtle

lucie = turtle.Turtle()
lucie.speed(0)

myscreen = turtle.getscreen()
myscreen.colormode(255)
myscreen.bgcolor("black")

lucie.pensize(4)

for i in range(15):
    lucie.pencolor(0, 250, 0)
    lucie.left(70)
    lucie.forward(20)
    lucie.backward(20) # revenir en arrière
    lucie.right(70) # revenir à l'angle initial

    lucie.penup()
    lucie.setx(lucie.xcor()+20) # se déplacer de 20 pour faire le brin suivant
    lucie.pendown()

turtle.done()
```

#### Exercices:

A partir du code de l'exemple.

- écrire une fonction `brin_d_herbe(angle, longueur, couleur, epaisseur)` qui dessine un brin d'herbe.

- écrire une fonction `ligne_d_herbe(position_initiale, nombre_brins, espacement)` qui utilise une boucle pour dessiner

- écrire une fonction `prairie(position_initiale, nombre_brins_x, nombre_brins_y, espacement)` qui utilise deux boucles pour dessiner une prairie (une grille de brin d'herbe comme dans l'exemple 8 de la partie précédente.

<!-- {{%expand "correction" %}}
```python
import turtle

lucie = turtle.Turtle()
lucie.speed(0)

myscreen = turtle.getscreen()
myscreen.colormode(255)
myscreen.bgcolor("black")

def brin_d_herbe(angle, longueur, couleur, epaisseur):
    lucie.pensize(epaisseur)
    lucie.pencolor(couleur)
    lucie.left(angle)
    lucie.forward(longueur)
    lucie.backward(longueur)
    lucie.right(70)

def ligne_d_herbe(nombre_brins, espacement):
    for x in range(nombre_brins):
        brin_d_herbe(70, 20, (0, 180, 0), 4)
        lucie.penup()
        lucie.setx(lucie.xcor()+espacement)
        lucie.pendown()

def prairie(position_x, position_y, nombre_brins_x, nombre_brins_y, espacement):
    lucie.penup()
    lucie.setposition(position_x, position_y)
    lucie.pendown()

    for y in range(nombre_brins_y):
        for x in range(nombre_brins_x):
            brin_d_herbe(70, 20, (0, 180, 0), 4)
            lucie.penup()
            lucie.setx(lucie.xcor()+espacement)
            lucie.pendown()

        lucie.penup()
        lucie.setx(position_x)
        lucie.sety(lucie.ycor()+espacement)
        lucie.pendown()


prairie(0, 0, 10, 10, 25)

turtle.done()
```
{{% /expand%}} -->


### Ajouter de l'aléatoire

Modifiez la fonction brin d'herbe et utilisez la fonction `random()` pour :

1. ajouter une variation aléatoire de 20 degrés sur l'angle du brin d'herbe.
2. choisir une couleur verte aléatoire différente pour chaque brin

<!-- {{%expand "correction" %}}
```python
import turtle
from random import random

lucie = turtle.Turtle()
lucie.speed(0)

myscreen = turtle.getscreen()
myscreen.colormode(255)
myscreen.bgcolor("black")

def brin_d_herbe(angle, longueur, couleur, epaisseur):
    lucie.pensize(epaisseur)
    lucie.pencolor(couleur)
    lucie.left(angle)
    lucie.forward(longueur)
    lucie.backward(longueur)
    lucie.right(angle)

def prairie(position_x, position_y, nombre_brins_x, nombre_brins_y, espacement):
    lucie.penup()
    lucie.setposition(position_x, position_y)
    lucie.pendown()

    for y in range(nombre_brins_y):
        for x in range(nombre_brins_x):
            angle = 60 + int(random()*20)
            vert = 50 + int(random()*200)
            couleur = (0, vert, 0)
            brin_d_herbe(angle, 20, couleur, 4)
            lucie.penup()
            lucie.setx(lucie.xcor()+espacement)
            lucie.pendown()

        lucie.penup()
        lucie.setx(position_x)
        lucie.sety(lucie.ycor()+espacement)
        lucie.pendown()


prairie(-125, -125, 10, 10, 25)

turtle.done()
```
{{% /expand%}} -->
