---
title: Jour 2 - Hash, Array & Iterators
layout: exercise
---

# Array to Hash

### Consigne

Ecrire une méthode dont la signature est `array_to_hash(array)`, qui prend un tableau en argument et retourne un hash.

### Exemple 

```ruby
hash = array_to_hash(["George", "Mickael", "Roger"])
p hash 
# => 
# { 
#   0 => "George",
#   1 => "Mickael",
#   2 => "Roger"
# }
```

# Iterators & Arrays

### Consigne 

Il s'agit dans cet exercice d'aller explorer la documentation de Ruby: https://ruby-doc.org/core-2.3.3/, et d'utiliser la bonne méthode (fonction) et le bon algorithme de façon à obtenir le résultat attendu. Vous devez remplir le contenu de chaque méthode, les signatures vous sont fournies.

N'hésitez pas à utiliser **IRB** !

```ruby
def sum_odd_indexed(array)
  # TODO: Faire la somme de tout les éléments dans le tableau dont l'index est un nombre impair
  # Astuce: Utiliser Enumerable#each_with_index
end

def even_numbers(array)
  # TODO: Extraire les nombres pairs d'un tableau et les retourner (dans un tableau aussi)
  # Astuce: Utiliser Enumerable#select
end

def short_words(array, max_length)
  # TODO: En partant d'un tableau de mots, retourner ceux qui sont moins long que `max_length`
  # Astuce: Utiliser Enumerable#reject
end

def first_under(array, limit)
  # TODO: Retourner le premier chiffre dans le tableau qui est en dessous de la `limit` 
  # Astuce: Utiliser Enumerable#find
end

def add_bang(array)
  # TODO: En partant d'un tableau de mots, retourner un nouveau tableau avec un `!` à la fin de chaque mot.
  # Astuce: Utiliser Enumerable#map
end

def array_ordered(array)
  # TODO: En partant d'un tableau de mots, retourner ce tableau trié dans l'ordre alphabétique
  # Astuce: N/A
end

def array_together(array)
  # TODO: En partant d'un tableau de mots, concatenez tous les éléments du tableau en une chaîne de caractère, chaque élément séparé par une `,`.
  # Astuce: N/A
end

```
