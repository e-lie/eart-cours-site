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

Nous allons voir ici le codage numérique d'image le plus simple: on l'appelle **bitmap**. C'est aussi un format d'image => fichier **.bmp**.

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

