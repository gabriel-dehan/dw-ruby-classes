---
title: Jour 1 - Variables, Méthodes & Types de données
layout: exercise
---

# Exercice 1

### Consigne

Le but est de permuter deux variables. En partant de:

```ruby
question = "La vie ?"
answer = 42
```

Permutez de **deux façons différentes** le contenu de ces deux variables. 
Notre but est donc d'avoir:

```ruby 
# question => 42
# answer   => "La vie ?"
```


# Exercice 2

### Consigne

Quelle est la différence entre ?

```ruby
# 1
a = 12
b = 14
c = a + b

puts c
```
```ruby
# 2
a = "12"
b = "14"
c = a + b

puts c
```
```ruby
# 3
a = 12
b = "14"
c = a + b

puts c
```

Quel est le résultat retourné à chaque fois ? Pourquoi ?


### Resources & Astuces

Utilisez **IRB** pour tester le code !


# Exercice 3

### Consigne

#### Première étape

Ecrivez une méthode qui prend un prénom, un nom et un age et retourne une phrase de présentation.
La signature de la méthode est la suivante: **`introduce_me(first_name, last_name, age)`**.
Elle devra retourner une **`String`** que vous stockerez dans une variable avant de l'afficher à l'écran.

#### Deuxième étape

En utilisant cette méthode, composez un programme qui demande, dans le terminal, à l'utilisateur son prénom, nom et age et lui affichera en retour la phrase de présentation retournée par la méthode **`introduce_me()`**.

#### Troisième étape

Parfois, les utilisateurs oublient de mettre une capitale à leur prénom ou nom de famille. Réglez ce problème ;)

