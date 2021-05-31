---
title: 10 - Continuer avec les tortues
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

Exercice: avec une boucle for dessinez 17 carrés de tailles 10, 20 jusqu'à 170.

### Exemple 2: fonction d'étoile multicolore aléatoire

```python
import turtle
from random import random

myscreen = turtle.getscreen()
myscreen.colormode(255)

smart = turtle.Turtle()

def couleur_aleatoire():
    rouge = int(random()*255)
    vert = int(random()*255)
    bleu = int(random()*255)
    return (rouge, vert, bleu)

def etoile(longueur_cote, couleur_crayon, taille_crayon):
    spiral = turtle.Turtle()
    spiral.pencolor(couleur_crayon)
    spiral.pensize(taille_crayon)
    for i in range(20):
        spiral.forward(i * longueur_cote)
        spiral.right(144)

etoile(10, couleur_aleatoire(), 2)
etoile(30, couleur_aleatoire(), 5)

turtle.done()
```

<!-- TODOOOOOO  faire de la décomposition fonctionnelle (inverser l'ordre) en commençant par des fonctions -->

### Herbes partie 0: se préparer et dessiner quelques herbes

```python
import turtle

lucie = turtle.Turtle()
lucie.speed(0)

myscreen = turtle.getscreen()
myscreen.colormode(255)
myscreen.bgcolor("black")
myscreen.screensize(300, 300)

lucie.pensize(4)

for i in range(15):
    lucie.pencolor(0, 250, 0)
    lucie.left(70)
    lucie.forward(20)
    lucie.backward(20)
    lucie.right(70)

    lucie.setx(lucie.xcor()+20)

turtle.done()
```

### Herbes partie 1: lever le crayon et paver l'image avec des coordonnés

```python
import turtle

lucie = turtle.Turtle()
lucie.speed(0)

myscreen = turtle.getscreen()
myscreen.colormode(255)
myscreen.bgcolor("black")
myscreen.screensize(300, 300)

lucie.pensize(4)

+ lucie.setposition((-150, -150))

+ for j in range(6):
    for i in range(15):
        lucie.pencolor(0, 250, 0)
        lucie.left(70)
        lucie.forward(20)
+         lucie.penup()
        lucie.backward(20)
        lucie.right(70)
        lucie.setx(lucie.xcor()+20)
+         lucie.pendown()
        
+     lucie.penup()
+     lucie.sety(lucie.ycor()+50)
+     lucie.setx(-150)
+     lucie.pendown()

+ lucie.penup()
+ lucie.home()
+ lucie.setposition(-150, 150)
+ lucie.pendown()

+ for i in range(4):
+     lucie.forward(300)
+     lucie.right(90)

turtle.done()
```
### Herbes partie 2: ajouter des variables

```python
import turtle

lucie = turtle.Turtle()
lucie.speed(0)
myscreen = turtle.getscreen()
myscreen.colormode(255)
myscreen.bgcolor("black")
myscreen.screensize(300, 300)

lucie.pensize(4)
lucie.setposition((-150, -150))

+ longueur_brin = 20
+ angle_brin = 70
+ couleur_vert_brin = 250

for j in range(6):
    for i in range(15):
        + lucie.pencolor(0, couleur_vert_brin, 0)
        + lucie.left(angle_brin)
        + lucie.forward(longueur_brin)
        lucie.penup()
        + lucie.backward(longueur_brin)
        + lucie.right(angle_brin)
        lucie.setx(lucie.xcor()+20)
        lucie.pendown()
        
    lucie.penup()
    lucie.sety(lucie.ycor()+50)
    lucie.setx(-150)
    lucie.pendown()

lucie.penup()
lucie.home()
lucie.setposition(-150, 150)
lucie.pendown()

for i in range(4):
    lucie.forward(300)
    lucie.right(90)

turtle.done()
```
### Herbes partie 3 ajouter une couleur aléatoire

```python
import turtle
from random import random


lucie = turtle.Turtle()
lucie.speed(0)
myscreen = turtle.getscreen()
myscreen.colormode(255)
myscreen.bgcolor("black")
myscreen.screensize(300, 300)

lucie.pensize(4)
lucie.setposition((-150, -150))

longueur_brin = 20
angle_brin = 70

for j in range(6):
    for i in range(15):
        + couleur_vert_brin = int(random()*250)+5
        lucie.pencolor(0, couleur_vert_brin, 0)
        
        lucie.left(angle_brin)
        + lucie.forward(longueur_brin)
        lucie.penup()
        lucie.backward(longueur_brin)
        lucie.right(angle_brin)
        lucie.setx(lucie.xcor()+20)
        lucie.pendown()
        
    lucie.penup()
    lucie.sety(lucie.ycor()+50)
    lucie.setx(-150)
    lucie.pendown()

lucie.penup()
lucie.home()
lucie.setposition(-150, 150)
lucie.pendown()

for i in range(4):
    lucie.forward(300)
    lucie.right(90)

turtle.done()
```
### Herbes partie 4: ajouter une orientation et longueur aléatoire

```python
import turtle
from random import random


lucie = turtle.Turtle()
lucie.speed(0)
myscreen = turtle.getscreen()
myscreen.colormode(255)
myscreen.bgcolor("black")
myscreen.screensize(300, 300)

lucie.pensize(4)
lucie.setposition((-150, -150))

base_longueur_brin = 20
variation_longueur_brin = 25
base_angle_brin = 70
variation_angle_brin = 20

for j in range(6):
    for i in range(15):
        angle_brin = int(random()*variation_angle_brin)+base_angle_brin
        longueur_brin = int(random()*variation_longueur_brin)+base_longueur_brin
        couleur_vert_brin = int(random()*250)+5
        
        lucie.pencolor(0, couleur_vert_brin, 0)
        
        lucie.left(angle_brin)
        lucie.forward(longueur_brin)
        lucie.penup()
        lucie.backward(longueur_brin)
        lucie.right(angle_brin)
        lucie.setx(lucie.xcor()+20)
        lucie.pendown()
        
    lucie.penup()
    lucie.sety(lucie.ycor()+50)
    lucie.setx(-150)
    lucie.pendown()

lucie.penup()
lucie.home()
lucie.setposition(-150, 150)
lucie.pendown()

for i in range(4):
    lucie.forward(300)
    lucie.right(90)

turtle.done()
```

<!-- ### Herbes partie 5: découper notre code en fonctions -> faire dans l'autre sens -->
