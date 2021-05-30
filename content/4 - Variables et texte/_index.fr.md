---
title: 3 - Les variables en Python 
weight: 2
---

### Exemple

```python
message1 = "Bonjour à toutes !"
message2 = "Combien font 6 x 7 ?"
reponse = 6 * 7

print(message1)
print(message2)
print(reponse)
```


![sorcery](../../../../images/python/sorcery.jpg)

### Principe

- Les variables sont des abstractions de la mémoire
- Une étiquette collée apposée sur une partie de la mémoire : nom pointe vers un contenu
- Différent du concept mathématique

![](../../../../images/python/memory2.png)



### 1.3. Déclaration, utilisation

- En python : déclaration implicite
- Ambiguité : en fonction du contexte, `x` désigne soit le contenant, soit le contenu...

```python
x = 42     # déclare (implicitement) une variable et assigne une valeur
x = 3.14   # ré-assigne la variable avec une autre valeur
y = x + 2  # déclare une autre variable y, à partir du contenu de x
print(y)   # affichage du contenu de y
```

### Nommage

- Caractères autorisés : caractères alphanumériques (`a-zA-Z0-9`) et `_`.
- **Les noms sont sensibles à la casse** : `toto` n'est pas la même chose que `Toto`!
- (Sans commencer par un chiffre)

### Comparaison de différentes instructions

Faire un calcul **sans l'afficher ni le stocker nul part**:

```python
6*7
```

Faire un calcul et **l'afficher dans la console**:

```python
print(6*7)
```

Faire un calcul et **stocker le résultat dans une variable `r`** pour le réutiliser plus tard

```python
r = 6*7
```



### Opérations mathématiques

```python
2 + 3   # Addition
2 - 3   # Soustraction
2 * 3   # Multiplication
2 / 3   # Division
2 % 3   # Modulo
2 ** 3  # Exponentiation
```


# Interactivité simple

En Python simple, il est possible de demander une information à l'utilisateur
avec `input("message")`

```python
reponse = input("Combien font 6 fois 7 ?")
```

N.B. : ce que renvoie `input()` est une **chaîne de caractère !** (= du texte pas un entier)

Demo dans Thonny

### Exercices pratique

- Ouvrir le logiciel `thonny`.

- Afficher le texte `Ce cours est bientôt terminé` avec `print`.
- Enregistrez dans le fichier `exercice1_1.py`.

{{% expand "exercice1_1.py" %}}

```python
print("Ce cours est bientôt terminé.")
```

{{% /expand %}}

- Afficher le texte `Je suis rangé dans une variable` en le rangeant dans une variable nommée `mavariable`.
- Enregistrez dans le fichier `exercice1_2.py`.

{{% expand "exercice1_2.py" %}}

```python
variable = "Je suis rangé dans une variable"
print(variable)
```

{{% /expand %}}

- Afficher le résultat du calcul 4 x 5.
- Enregistrez dans le fichier `exercice1_3.py`.

{{% expand "exercice1_3.py" %}}

```python
print(4*5)
```

{{% /expand %}}

- Afficher le résultat de 10 x 10 en le rangeant dans une variable.
- Enregistrez dans le fichier `exercice1_4.py`.

{{% expand "exercice1_1.py" %}}

```python
resultat = 10 * 10
print(resultat)
```

{{% /expand %}}

- Demander l'âge de l'utilisateur, puis calculer et afficher l'âge qu'il aura dans deux ans et afficher le résultat.

{{% expand "age1.py" %}}

```python
age = input("Quel est votre age ?")
print("Dans deux ans vous aurez " + str(age + 2) + " ans." )
```

{{% /expand %}}

- Calculer l'age dans deux ans, mais cette fois en demandant l'année de naissance (approximativement, sans tenir compte du jour et mois de naissance...).

{{% expand "age2.py" %}}

```python
annee_naissance = int(input("Donnez moi votre année de naissance."))
age = 2021 - annee_naissance + 2
print("Dans deux ans vous aurez " + str(age) + " ans.")
```

{{% /expand %}}

- Demander un mot à l'utilisateur. Afficher la longueur du mot avec un message tel que "Ce mot fait X caractères !"

{{% expand "correction" %}}

```python
mot = input("Donnez moi un mot")
print(mot.length())
```

{{% /expand %}}
