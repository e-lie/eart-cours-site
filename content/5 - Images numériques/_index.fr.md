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
imgbase = Image.open("./baseimg/fantasy-persona.jpg")
pxbase = imgbase.load()
```

Attention ! : il faut préciser ou enregistrer l'image avec le chemin de son dossier et son nom.

## Exercices pratiques

- Créer une image de 30x30 pixel et mettre tous les pixels à rouge.
- Créer une image de 255x255 et mettre comme couleur rouge et verte la position du pixel (0 pour le bleu).
- Ouvrir l'image résultante dans le logiciel krita.
- Créer une image de 10x10 ou le premier pixel est rouge, le deuxième est vert, le troisième bleu, le quatrième rouge etc en continuant ainsi.
- Ouvrir l'image dans krita.
