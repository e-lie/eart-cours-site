---
title: 6 - Les boucles
weight: 2
---

# 3. Boucles

Répéter des opérations est le coeur de l'informatique car l'ordinateur peut répéter très vite et sans se fatiguer. Répéter des opérations et les combiner avec des conditions permet d'écrire presque tous les traitements automatiques imaginables.

On peut traduire la boucle Python `for element in collection:` en français par "Pour chaque élément de ma collection répéter ...". Nous avons donc besoin d'une "collection" pour l'utiliser. Classiquement on peut utiliser une **liste** python pour cela:

```python
ma_liste = [7, 2, -5, 4]

for entier in ma_liste:
    print(entier)
```

Pour générer rapidement une liste  d'entiers et ainsi faire un nombre défini de tours de boucle on utilise classiquement la fonction `range()`

```python
print(range(10))

for entier in range(10):
    print(entier) # Afficher les 10 nombres de 0 à 9
```

```python
for entier in range(1, 11):
    print(entier) # Afficher les 10 nombres de 1 à 10
```


## `continue` et `break`

`continue` permet de passer immédiatement à l'itération suivante

`break` permet de sortir immédiatement de la boucle


```python
for i in range(0,10):
    if i % 2 == 0:
        continue

    print("En ce moment, i vaut " + str(i))
```

-> Affiche le message seulement pour les nombres impairs


```python
for i in range(0,10):
    if i == 7:
        break

    print("En ce moment, i vaut " + str(i))
```

-> Affiche le message pour 0 à 6

# Exercices pratiques

- Affichez avec une boucle les entiers de 1 à 10.

{{% expand "correction" %}}

```python
for entier in range(10):
    print(entier+1)
```

{{% /expand %}}

- Affichez avec une boucle les entiers de 1 à 20 s'ils sont pairs.

{{% expand "correction" %}}

```python
for index in range(1,21):
    if index % 2 == 0:
        print(index)
```

{{% /expand %}}

- Affichez 3 fois les entiers pairs de 1 à 10 en utilisant deux boucles l'une dans l'autre.

{{% expand "correction" %}}

```python
for n in range(3):
    for m in range(10):
        print(m+1)
```

{{% /expand %}}

