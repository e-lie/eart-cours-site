---
title: 5 - Images numériques 
weight: 2
---


L'ordinateur est une machine à calculer très puissante.

- Il peut manipuler uniquement des nombres et des groupes de nombres:
    - Le texte numérique est composé de nombres.
    - Les images numériques le sont aussi.
    - Tout comme la musique numérique.
    - Etc.
- C'est le véritable sens du **mot numérique/digital** : un objet codé sous forme de nombres.

Pour parler de la façon dont on représente un objet sous forme numérique on parle de **codage numérique** en français.

Nous allons voir ici le codage numérique d'image le plus simple : on l'appelle couramment **bitmap**. C'est aussi un format d'image => fichier **.bmp**.

### Image Bitmap

- Une image bitmap est un **tableau de pixels**.
- Chaque pixel a une **position** et une **couleur**.
- La position est composée de deux nombres:
    - la coordonnée **x** et la coordonnée **y**.
    - pour une image de 10x10 pixel **x** est compris entre **0 et 9** et **y** est compris entre **0 et 9**.
- Exemple d'une image en noir et blanc (deux couleurs 0 et 1):

![](../../../../images/eart/how-bitmap-images-are-stored.png)

#### Image en couleur RGB

- La couleur est composée de trois nombres: **red** (quantité de rouge), **green** (quantité de vert) et **blue** (quantité de bleu)
- On parle d'image RVB ou plutôt RGB (en anglais).

![](../../../../images/eart/220px-RGB_sliders.svg.png)

- Pour créer les autres couleurs on mélange ces quantités de couleur selon selon le modèle du mélange de la lumière.

![](../../../../images/eart/220px-AdditiveColor.svg.png)
![](../../../../images/eart/rgb-examples.png)

## Images en Python

Pour manipuler des images en Python il existe pleins de possibilité. La plus classique est la **bibliothèque (library)** appelée **PIL (Python Imaging Library)**.

- Pour Utiliser la PIL il faut l'**importer** en ajoutant une ligne au début du fichier de code la ligne:

```python
from PIL import Image
```

### Créer une nouvelle image

```python
img = Image.new( 'RGB', (255,255), "black") # create a new black image
pixels = img.load() # create the pixel map
```

### Parcourir tous les pixels de l'image pour changer la couleur

```python
for x in range(img.size[0]): # Pour chaque colonne de pixel
    for y in range(img.size[1]): # Pour chaque ligne de pixel
        pixels[x,y] = (255,255,255) # Modifier la couleur du pixel courant
```

### Afficher une image

```python
img.show()
```

### Enregistrer une image

```python
img.save("~/Desktop/image1.png")
```

Attention ! : il faut préciser ou enregistrer l'image avec le chemin de son dossier.

### Charger une image existante

```python
img_fantasy = Image.open("./baseimg/fantasy-persona.jpg")
pixels = img_fantasy.load()
```

Attention ! : il faut préciser ou enregistrer l'image avec le chemin de son dossier et son nom.

## Exercices pratiques

- `exercice5_1.py` : Créer une image de 30x30 pixel et mettre tous les pixels à jaune. affichez l'image avec `img.show()`

{{% expand "exercice5_1.py" %}}

```python
from PIL import Image

img = Image.new("RGB", (30, 30), "black")
pixels = img.load()

for x in range(img.size[0]):
    for y in range(img.size[1]):
        pixels[x, y] = (255, 255, 0) # le jaune RGB est un mélange de rouge et de vert.

img.show()
```

{{% /expand %}}

- `exercice5_2.py` : Créer une image de 255x255 et mettre comme couleur rouge et verte la position du pixel (0 pour le bleu).
- Enregistrer l'image avec `img.save()` et l'ouvrir dans le logiciel krita. Zoomez pour voir les pixels.

{{% expand "exercice5_2.py" %}}

```python
from PIL import Image

img = Image.new("RGB", (255, 255), "black")
pixels = img.load()

for x in range(img.size[0]):
    for y in range(img.size[1]):
        pixels[x, y] = (x, y, 0) # le jaune RGB est un mélange de rouge et de vert.

img.save("./exercice5_2.bmp")
```

{{% /expand %}}

- `exercice5_3.py` : Créer une image de 10x10 ou le premier pixel est rouge, le deuxième est vert, le troisième bleu, le quatrième rouge etc en continuant ainsi.
- Enregistrez et ouvrir l'image dans krita.

{{% expand "exercice5_3.py" %}}

```python
from PIL import Image

img = Image.new("RGB", (255, 255), "black")
pixels = img.load()

color_counter = 1

for x in range(img.size[0]):
    for y in range(img.size[1]):
        if color_counter == 1:
            pixels[x, y] = (255, 0, 0)
        if color_counter == 2:
            pixels[x, y] = (0, 255, 0)
        if color_counter == 3:
            pixels[x, y] = (0, 0, 255)
        
        color_counter += 1
        if color_counter >= 4:
            color_counter = 1

img.save("./exercice5_3.bmp")
```

{{% /expand %}}

## Production d'une image avec un programme interactif.

- créer un nouveau programme.
- Importez PIL.Image
- Ajoutez la fonction `repeat` suivante (collez le code ci dessous dans votre programme):

```python
def repeat(imgbase, repeatx, repeaty):
    pxbase = imgbase.load()
    img = Image.new( 'RGB', (imgbase.size[0]*repeatx,imgbase.size[1]*repeaty), "black") # create a new black image
    pixels = img.load() # create the pixel map
    for repx in range(repeatx):
        for repy in range(repeaty):
            for x in range(imgbase.size[0]):    # for every col:
                for y in range(imgbase.size[1]):    # For every row
                        pixels[x+repx*imgbase.size[0], y+repy*imgbase.size[1]] = pxbase[x, y]
    return img
```
- Ouvrez l'une de vos images dans une variable imgbase.
- Utilisez la fonction `repeat` pour créer une nouvelle image dans une variable `img` qui est la répétition de `imgbase`

- Demandez à l'utilisateur du programme d'entrer le nom de l'image à ouvrir.
- Demander à l'utilisateur d'entrer le nombre de répétition horizontale (`repeatx`).
- Demander à l'utilisateur d'entrer le nombre de répétition verticale (`repeaty`).
- Demander à l'utilisateur d'entrer un nombre `taille_grille`.


- Mettez la couleur rouge à tous les pixels dont la position x est multiple de taille grille et dont la position y est aussi multiple de taille_grille.

- Affichez et enregistrez l'image.

- Lancez le programme et changer l'image ouverte et les paramètre repeat et taille_grille.

### Correction du programme

```python
from PIL import Image

def repeat(imgbase, repeatx, repeaty):
    pxbase = imgbase.load()
    img = Image.new( 'RGB', (imgbase.size[0]*repeatx,imgbase.size[1]*repeaty), "black") # create a new black image
    pixels = img.load() # create the pixel map
    for repx in range(repeatx):
        for repy in range(repeaty):
            for x in range(imgbase.size[0]):    # for every col:
                for y in range(imgbase.size[1]):    # For every row
                        pixels[x+repx*imgbase.size[0], y+repy*imgbase.size[1]] = pxbase[x, y]
    return img

nom_image = input("Quelle image ouvrir ?")
repetition_x = int(input("Combien repetition horizontale ?"))
repetition_y = int(input("Combien repetition verticale ?"))
taille_grille = int(input("Quelle taille de grille ?"))


imgbase = Image.open("./"+nom_image)

img = repeat(imgbase, repetition_x, repetition_y)
pixels = img.load()


for x in range(img.size[0]):
    for y in range(img.size[1]):
        if x % taille_grille == 0 or y % taille_grille == 0:
            pixels[x, y] = (200, 0, 0)

img.show()
img.save("./resultat.bmp")
```