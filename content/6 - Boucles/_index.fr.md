---
title: 4 - Le langage Python - Partie2
weight: 2
---


# 2. Conditions

Pour pouvoir écrire des applications il faut des techniques permettant de contrôler le déroulement du programme dans différentes directions, en fonction des circonstances. Pour cela, nous devons disposer d’instructions capables de tester une certaine condition et modifier le comportement du programme en conséquence.

La principale instruction conditionnelle est, en python comme dans les autres langages **impératifs**, le `if` (Si condition alors ...) assorti généralement du `else` (Sinon faire ...) et en python de la contraction `elif` de `else if` (Sinon, Si condition alors ...)e

###  Exemple

```python
x = int(input("Entrez un nombre entier"))
if x == 100:
    print("une centaine")
```



```python
a = int(input("Entrez un nombre entier"))
if a > 0 :
    print("a est positif")
elif a < 0 :
    print("a est négatif")
else:
    print("a est nul")
```

Attention à l'indentation !

Tout n'est pas nécessaire, par exemple on peut simplement mettre un `if` comme dans l'exemple 1.


### Autre exemple

```python
message = "bonjour à toutes"
if "bonjour" in message:
    print("c'est un message de bonjour")
```

### Écrire des conditions

```python
nombre == 1      # Égalité
nombre != 1      # Différence
nombre > 1       # Supérieur
nombre >= 1      # Supérieur ou égal
nombre < 1       # Inférieur
nombre <= 1      # Inférieur ou égal
```

### Combiner des conditions

```python
x = 2

print(x > 0) # vrai 
print(x > 0 and x == 2) # vrai et vrai donne vrai
print(x < 0 or x == 2) # faut ou vrai donne vrai
```

## Exercices

- Demandez un nombre et affichez "positif" s'il est supérieur ou égal à 0.

{{% expand "correction" %}}

```python
entier = input("Donnez moi un nombre entier (positif ou négatif).")
if entier >= 0:
    print("positif")
```

{{% /expand %}}


- Demander l'âge de l'utilisateur, puis affichez "votre age est pair" si l'age est divisible par 2. Si l'age est divisible par 3 affichez "votre age est divisible par 3" .

{{% expand "age3.py" %}}

```python
age = input("Quel est votre age ?")
if age % 2 == 0:
    print("votre age est pair.")
if age % 3 == 0:
    print("votre age est multiple de 3.")
```

{{% /expand %}}

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

