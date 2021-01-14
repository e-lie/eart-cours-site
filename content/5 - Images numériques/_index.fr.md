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

- `exercice5_1.py` : Créer une image de 30x30 pixel et mettre tous les pixels à rouge. affichez l'image avec `img.show()`
- `exercice5_2.py` : Créer une image de 255x255 et mettre comme couleur rouge et verte la position du pixel (0 pour le bleu).
- Enregistrer l'image avec `img.save()` et l'ouvrir dans le logiciel krita. Zoomez pour voir les pixels.
- `exercice5_3.py` : Créer une image de 10x10 ou le premier pixel est rouge, le deuxième est vert, le troisième bleu, le quatrième rouge etc en continuant ainsi.
- Enregistrez et ouvrir l'image dans krita.
- Exercice addition d'images:
    - Ouvrez deux petites images d'internet avec `Image.open()`
    - Créez une troisième image de 30x30.
    - Pour chaque pixel de cette troisième image prenez l'addition des pixels corespondant de chacune des deux images ouvertes image.

## Production d'une image avec un programme interactif.

- Créez un programme qui ouvre l'une de vos images.
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

- Demandez à l'utilisateur du programme d'entrer le nom de l'image à ouvrir
- Demander à l'utilisateur d'entrer le nombre de répétition horizontale (`repeatx`).
- Demander à l'utilisateur d'entrer le nombre de répétition verticale (`repeaty`).
- Ajoutez la fonction suivante pour ajouter deux couleurs:

```python
def rgb_add(rgb_tuple1, rgb_tuple2):
    return rgb_tuple1[0]+rgb_tuple2[0], rgb_tuple1[1]+rgb_tuple2[1], rgb_tuple1[2]+rgb_tuple2[2]
```

- Ajoutez la couleur `(200, 0, 0)` à tous les pixels multiples de 5.
- Ajoutez la couleur `(100, 200, 0)` à tous les pixels multiples de 7.